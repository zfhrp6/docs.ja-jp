---
title: インフラストラクチャの永続レイヤーの設計
description: '.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | インフラストラクチャの永続レイヤーの設計'
keywords: Docker, マイクロサービス, ASP.NET, コンテナー
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/08/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 76db5388c75d4eb3b5cc23c1e57cc391a15f2934
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2018
---
# <a name="designing-the-infrastructure-persistence-layer"></a>インフラストラクチャの永続レイヤーの設計

データ永続化コンポーネントは、マイクロサービス (つまり、マイクロサービスのデータベース) の境界内でホストされているデータへのアクセスを提供します。 内容としては、リポジトリや[作業単位](http://martinfowler.com/eaaCatalog/unitOfWork.html)クラス (カスタム EF DBContexts など) などのコンポーネントの実際の実装が含まれています。

## <a name="the-repository-pattern"></a>リポジトリ パターン

リポジトリは、データ ソースへのアクセスに必要なロジックをカプセル化するクラスまたはコンポーネントです。 リポジトリは一般的なデータ アクセス機能を一元管理して保守性を向上させ、ドメイン モデル レイヤーからデータベースにアクセスするためのインフラストラクチャやテクノロジを切り離します。 Entity Framework などの ORM を使用する場合、LINQ と厳密な型指定により、実装する必要があるコードが簡素化されます。 これによりデータ アクセスの組み込みではなく、データ永続化ロジックに集中できるようになります。

リポジトリ パターンは、ドキュメントが整備されたデータ ソース操作方法です。 Martin Fowler は、著書『[エンタープライズ アプリケーション アーキテクチャ パターン](https://www.amazon.com/Patterns-Enterprise-Application-Architecture-Martin/dp/0321127420/)』の中でリポジトリのことを次のように述べています。

リポジトリは、ドメイン モデル レイヤーとデータ マッピングの間を媒介するタスクを実行し、メモリ内のドメイン オブジェクト セットに似たような動作をする。 クライアント オブジェクトは宣言によってクエリを構築し、リポジトリに送信して回答を得る。 概念上、リポジトリはデータベースに格納されている一連のオブジェクトとオブジェクト上で実行可能な操作をカプセル化し、永続レイヤーに近い方法を提供する。 また、リポジトリは、作業ドメインとデータの割り当て、すなわちマッピングとの依存関係を明確かつ一方向に切り離すという目的をサポートする。

### <a name="define-one-repository-per-aggregate"></a>集約ごとにリポジトリを定義する

各集約または集約ルートに1 つのリポジトリ クラスを作成する必要があります。 ドメイン駆動設計パターンに基づくマイクロサービスでは、リポジトリはデータベースの更新に使用する唯一のチャネルです。 これは、リポジトリには集約ルートとの一対一の関係があるためで、これにより集約の不変性とトランザクションの一貫性が管理されます。 データベースのクエリは他のチャネルで実行することもできますが (CQRS アプローチに従って実行することも可能)、それは、クエリではデータベースの状態が変更されないためです。 トランザクション領域が更新の場合は、常にリポジトリと集約ルートで制御する必要があります。

基本的に、リポジトリでは、データベースから取得されたデータをドメイン エンティティの形式でメモリ内に設定することができます。 メモリ内に設定されたエンティティは、トランザクションによって変更し、再度データベースに保存することができます。

前述したように、CQS/CQRS アーキテクチャ パターンを使用している場合、Dapper を使用した単純な SQL ステートメントによって実行されるドメイン モデルからの副クエリによって最初のクエリが実行されます。 この方法は、必要な任意のテーブルを照会および結合可能で、クエリが集約からのルールによって制限されないため、リポジトリよりはるかに柔軟です。 その場合、データはプレゼンテーション層またはクライアント アプリに遷移します。

ユーザーが変更を行うと、更新データはクライアント アプリまたはプレゼンテーション層からアプリケーション層 (Web API サービスなど) に移動します。 コマンド ハンドラーでコマンド (とデータ) を受信したら、リポジトリを使用して、更新するデータをデータベースから取得します。 メモリ内で、コマンドを使用して渡された情報を更新した後、トランザクションによりデータベース内のデータ (ドメイン エンティティ) を追加または更新します。

図 9-17 に示すように、各集約ルートに定義するリポジトリは 1 つだけであることに注意してください。 集約内のすべてのオブジェクト間のトランザクションの一貫性を維持するという集約ルートの目標を達成するため、データベース内の各テーブルのリポジトリは作成しません。

![](./media/image18.png)

**図 9-17**。 リポジトリ、集約、およびデータベース テーブル間のリレーションシップ

### <a name="enforcing-one-aggregate-root-per-repository"></a>リポジトリごとに 1 つの集約ルートを適用

リポジトリ設計を実装する際に、集約ルートのみにリポジトリを設定するというルールを適用することが重要な場合があります。 操作するエンティティの型を制約するジェネリック型または基本型のリポジトリを作成し、IAggregateRoot マーカー インターフェイスを設定することができます。

このように、インフラストラクチャ レイヤーで実装されている各リポジトリ クラスに独自のコントラクトまたはインターフェイスが実装されます (次のコードを参照)。

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class OrderRepository : IOrderRepository
    {
```

リポジトリの各インターフェイスには、ジェネリック IRepository インターフェイスが実装されます。

```csharp
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);
    // ...
}
```

ただし、コードが、規則を適用する優れた方法として、特定の集約を対象とするリポジトリを使用している明示的なので、汎用的なリポジトリの種類を実装すること、1 つの集約に各リポジトリを関連付ける必要があります。 これは、次のコードのように、そのジェネリックを IRepository 基底インターフェイスで実装することで簡単に行えます。

```csharp
  public interface IRepository<T> where T : IAggregateRoot
```

### <a name="the-repository-pattern-makes-it-easier-to-test-your-application-logic"></a>アプリケーション ロジックのテストを容易にするリポジトリ パターン

リポジトリ パターンを利用すると、単体テストでアプリケーションを簡単にテストすることができます。 単体テストの対象はインフラストラクチャではなく、コードのみであるため、リポジトリの抽象化により目的を達成しやすくなります。

前のセクションで説明したように、リポジトリ インターフェイスをドメイン モデル レイヤーに定義および配置し、アプリケーション レイヤー (たとえば Web API マイクロサービス) が、実際のリポジトリ クラスを実装しているインフラストラクチャ レイヤーに直接依存しないようにすることをお勧めします。 これにより、Web API のコント ローラーで依存関係の挿入を使用して、データベースのデータではなく疑似データを返すモック リポジトリを実装できます。 このような分離アプローチでは、データベースへの接続を必要とせず、アプリケーションのロジックだけをテストする単位テストを作成し、実行することができます。

データベースに対して膨大なテストを実行することには、データベースへの接続が失敗する可能性があることに加え、さらに大きな 2 つの理由から問題があります。 その一つは、テスト量の多さにより時間がかかる可能性があることです。 もう一つは、データベースのレコードが変更され、テスト結果に影響して、データの一貫性がなくなる可能性があるということです。 データベースに対するテストは単体テストではなく、統合テストです。 多数の単体テストを高速で実行する必要がありますが、データベースに対する統合テストは大量に行う必要はありません。

単体テストの問題の分離という観点から、ロジックはメモリ内のドメイン エンティティで動作します。 ドメイン エンティティはリポジトリ クラスで提供されるものと想定します。 また、ロジックによって変更されたドメイン エンティティは、リポジトリ クラスに適切に保存されるものと想定します。 ここでの重要なポイントは、単体テストはドメイン モデルとそのドメイン ロジックに対して作成するということです。 集約ルートは DDD の主な整合性境界です。

### <a name="the-difference-between-the-repository-pattern-and-the-legacy-data-access-class-dal-class-pattern"></a>リポジトリ パターンと、従来のデータ アクセス クラス (DAL クラス) パターンの違い

データ アクセス オブジェクトは、データ アクセスおよび永続化操作を記憶域に対して直接実行します。 リポジトリは、メモリ内の作業単位オブジェクトの操作対象データにマークを付け (例: DbContext を使用する場合の EF)、更新はすぐには実行しません。

作業単位は複数の挿入、更新、または削除操作が関与する単一のトランザクションとして表されます。 つまり、特定のユーザー操作 (たとえば Web サイトへの登録) に対して、すべての挿入、更新、および削除のトランザクションが 1 つのトランザクションとして処理されることを意味します。 これは、複数のデータベース トランザクションを対話方法で処理するよりも効率的です。

これらの複数の永続化操作は、後でアプリケーション レイヤーのコードが命令を発行したときに、1 アクションで実行されます。 実際のデータベース記憶域にメモリ内の変更を適用する決定は、通常、[作業単位パターン](http://martinfowler.com/eaaCatalog/unitOfWork.html)に基づいて行われます。 EF には、作業単位パターンは DBContext として実装されます。

多くの場合、このパターンまたは記憶域に対する操作の適用方法により、アプリケーションのパフォーマンスを向上させ、不整合の可能性を低減することができます。 また、意図したすべての操作が 1 つのトランザクションの一部としてコミットされるので、データベース テーブル内でブロックされるトランザクションが少なくなります。 これは、データベースに対して多数の単独の操作を実行する場合と比べて効率的です。 そのため、小規模な単独のトランザクションを多数実行するのではなく、同じトランザクション内で複数の更新操作をグループ化することにより、選択した ORM でデータベースに対する実行を最適化できます。

### <a name="repositories-should-not-be-mandatory"></a>リポジトリは必須ではない

カスタム リポジトリは、前述の理由により便利であり、eShopOnContainers の順序付けマイクロサービスで採用されているアプローチですが、 DDD 設計の実装、または .NET での開発全般に不可欠なパターンではありません。

たとえば、このガイドに対するフィードバックを直接提供してくれた Jimmy Bogard は次のように述べています。

おそらく、これは私の最大のフィードバックになるでしょう。 私はリポジトリが好きではありません。その主な理由は、基本となる永続化メカニズムの重要な詳細が隠ぺいされていることです。 私がコマンドに MediatR を採用する理由もそこにあります。 永続レイヤーの機能をフルに活用し、集約ルートにドメイン動作のすべてをプッシュすることができます。 通常は、リポジトリでのシミュレーションを行いたくないので、実際のデータで統合テストを実行する必要があります。 CQRS を利用すれば、もうリポジトリは不要です。

リポジトリが便利であることはわかっていますが、集約パターンやリッチ ドメイン モデルとは異なり、DDD においてリポジトリは不可欠ではありません。 したがって、リポジトリ パターンは使用しても、しなくても、かまいません。

## <a name="the-specification-pattern"></a>仕様パターン

仕様パターン (正式名称はクエリ仕様パターン) は、並べ替え/ページング ロジックを指定可能なクエリ定義を配置する場所として設けられたドメイン駆動設計パターンです。

仕様パターンではクエリをオブジェクトに定義します。 たとえば、必要な入力パラメーター (pageNumber、pageSize、filter など) を受け取る PagedProduct 仕様を作成することで、製品を検索するページ指定クエリをカプセル化できます。 その後、Repository の任意のメソッド (通常は List() オーバーロード) 内で、ISpecification を受け取り、その仕様に基づいて予想されるクエリを実行します。

このアプローチにはいくつかの利点があります。

* 仕様には議論の余地のある名前 (単なる一連の LINQ 式ではなく) が付いています。

* 仕様単独で単位テストを実行し、適切であることを確認できます。 同様の動作が必要な場合に、仕様を容易に再利用できます。 たとえば、MVC ビュー アクションと Web API アクション、およびさまざまなサービスで仕様を再利用できます。

* 仕様は、返されるデータの構造の記述にも使用できるため、クエリで必要なデータだけを返すことができます。 これにより、Web アプリケーションの遅延読み込み (通常はお勧めできない操作) の必要がなくなり、リポジトリの実装にこうした繁雑な詳細を取り入れずに済みます。

一般的な Specification (仕様) インターフェイスの例として、[eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb ) から抜粋した次のコードをご覧ください。

```csharp
// https://github.com/dotnet-architecture/eShopOnWeb 
public interface ISpecification<T>
{
    Expression<Func<T, bool>> Criteria { get; }
    List<Expression<Func<T, object>>> Includes { get; }
    List<string> IncludeStrings { get; }
}
```

次のセクションでは、仕様パターンを Entity Framework Core 2.0 で実装する方法と、任意の Repository (リポジトリ) クラスから使用する方法を説明します。

**重要な注意事項:**仕様パターンは、次の「その他の技術情報」のセクションに示されているように、さまざまな方法で実装できる古いパターンです。 パターンやアイデアとしては古いアプローチがわかりやすいかもしれませんが、Linq や式のような最新の言語機能を利用していない古い実装には注意が必要です。

## <a name="additional-resources"></a>その他の技術情報

### <a name="the-repository-pattern"></a>リポジトリ パターン

-   **Edward Hieatt、Rob Mee。リポジトリ パターン。**
    [*http://martinfowler.com/eaaCatalog/repository.html*](http://martinfowler.com/eaaCatalog/repository.html)

-   **リポジトリ パターン**
    [*https://msdn.microsoft.com/library/ff649690.aspx*](https://msdn.microsoft.com/library/ff649690.aspx)

-   **リポジトリ パターン: データ持続性の抽象化**
    [*http://deviq.com/repository-pattern/*](http://deviq.com/repository-pattern/)

-   **Eric Evans。Domain-Driven Design: Tackling Complexity in the Heart of Software (ドメイン駆動設計: ソフトウェア中心部の複雑さへの取り組み)。** (予約以外の場合は、リポジトリ パターンの詳細についてにが含まれています) [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

### <a name="unit-of-work-pattern"></a>Unit of Work パターン

-   **Martin Fowler。作業のパターンの単位。**
    [*http://martinfowler.com/eaaCatalog/unitOfWork.html*](http://martinfowler.com/eaaCatalog/unitOfWork.html)

<!-- -->

-   **ASP.NET MVC アプリケーションでの Repository および Unit of Work パターンの実装**
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)

### <a name="the-specification-pattern"></a>仕様パターン

-   **仕様のパターン。**
    [*http://deviq.com/specification-pattern/*](http://deviq.com/specification-pattern/)

-   **Evans, Eric (2004 年)。「Domain Driven Design」(ドメイン駆動設計)。Addison-Wesley. p. 224.**

-   **「Specifications」(仕様)。Martin ファウラー**
    [*https://www.martinfowler.com/apsupp/spec.pdf/*](https://www.martinfowler.com/apsupp/spec.pdf)

>[!div class="step-by-step"]
[前へ] (domain-events-design-implementation.md) [次へ] (infrastructure-persistence-layer-implemenation-entity-framework-core.md)
