---
title: "インフラストラクチャの永続性レイヤーをデザイン"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |インフラストラクチャの永続性レイヤーをデザイン"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: ce0f1d608eed909a7707f3c580afc5253f3eef06
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="designing-the-infrastructure-persistence-layer"></a>インフラストラクチャの永続性レイヤーをデザイン

データの永続化コンポーネントは、マイクロ サービス (つまり、マイクロ サービスのデータベース) の境界内でホストされているデータへのアクセスを提供します。 リポジトリなどのコンポーネントの実際の実装が含まれていると[作業単位](http://martinfowler.com/eaaCatalog/unitOfWork.html)カスタム EF DBContexts などのクラスです。

## <a name="the-repository-pattern"></a>リポジトリ パターン

リポジトリは、クラスまたはデータ ソースへのアクセスに必要なロジックをカプセル化するコンポーネントです。 これらには、一般的なデータ アクセス機能を保守性の向上を提供して、インフラストラクチャまたはドメイン モデル レイヤーからデータベースにアクセスするためのテクノロジを切り離すことが一元管理します。 Entity Framework と同様に、ORM を使用する場合は LINQ と厳密な型指定のおかげで実装する必要がありますのあるコードが簡素化されます。 これによりデータではなく、データの永続化ロジックに集中することの組み込みにアクセスします。

リポジトリ パターンは、データ ソースを操作の詳しい解説方法です。 ブックで[エンタープライズ アプリケーションのアーキテクチャのパターン](https://www.amazon.com/Patterns-Enterprise-Application-Architecture-Martin/dp/0321127420/)、次のように Martin ファウラーにリポジトリがについて説明します。

リポジトリは、メモリ内のドメイン オブジェクトのセットに似た方法で動作する、ドメイン モデル レイヤーとデータのマッピングの間の媒介のタスクを実行します。 クライアント オブジェクトは、宣言によってクエリの作成し、回答のリポジトリに送信します。 概念的には、リポジトリは、永続性レイヤーに近い方法を提供するのには、実行できる操作、データベースに格納されているオブジェクトのセットをカプセル化します。 リポジトリはまた、明確にし、一方向で、作業ドメインとデータの割り当ての間の依存関係を分離またはマッピングの目的をサポートします。

### <a name="define-one-repository-per-aggregate"></a>集計ごとに 1 つのリポジトリを定義します。

各集計または集計ルートには、1 つのリポジトリ クラスを作成する必要があります。 ドメイン ベースのデザイン パターンに基づくマイクロ サービス、チャネルの唯一のデータベースの更新に使用する必要がありますはリポジトリをする必要があります。 これは、集計の不変性とトランザクションの一貫性を制御する集計ルートと一対一のリレーションシップがあるためです。 他のデータベースを照会することがチャンネル (CQRS アプローチに従って行うことができます) と、クエリでは、データベースの状態が変更されないためです。 ただし、トランザクション領域 — 更新プログラム-リポジトリと集計のルートで常に制御する必要があります。

基本的には、リポジトリには、ドメイン エンティティの形式でデータベースから取得されるメモリ内のデータを設定することができます。 後のエンティティは、メモリ内では、それらを変更して、トランザクションを使用してデータベースにし、永続化ことができます。

前述の CQS/CQRS アーキテクチャ パターンを使用している場合、Dapper を使用して単純な SQL ステートメントによって実行されるドメイン モデルで不足側クエリによって最初のクエリが実行されます。 この方法は、はるかに必要なクエリを実行して任意のテーブルを結合するので、リポジトリよりも柔軟性、および集計からこれらのクエリがルールによって制限されません。 そのデータは、プレゼンテーション層またはクライアント アプリに移動します。

変更を行い、データを更新するが、アプリケーション層 (Web API サービスなど) にクライアント アプリまたはプレゼンテーション層から得られます。 コマンド ハンドラーで (データ) を使用したコマンドを受信するとリポジトリを使用してデータベースから更新するデータを取得します。 メモリ内で、コマンドを使用して渡された情報を更新して、しを追加または更新トランザクションを使用して、データベース内のデータ (ドメイン エンティティ)。

必要がありますを強調するもう一度を図 9-17 ように、各集計ルートに 1 つだけのリポジトリを定義する必要があります。 集計内のすべてのオブジェクト間のトランザクションの一貫性を維持するために、集計のルートの目標を達成するには、データベース内の各テーブルのリポジトリは作成しないでです。

![](./media/image18.png)

**図 9-17**です。 リポジトリ、集計、およびデータベースのテーブル間のリレーションシップ

### <a name="enforcing-one-aggregate-root-per-repository"></a>リポジトリごとに 1 つの集計ルートを適用します。

集計ルートのみがリポジトリ ルールがによって適用されるように、リポジトリ設計を実装する価値があります。 連携して利用できるようにする IAggregateRoot マーカー インターフェイスには、エンティティの型を制約するジェネリック、またはベースのリポジトリの種類を作成することができます。

このため、インフラストラクチャ レイヤーで実装されている各リポジトリ クラスを実装する独自の契約またはインターフェイスを次のコードに示すように。

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class OrderRepository : IOrderRepository
    {
```

特定のリポジトリの各インターフェイスには、ジェネリック IRepository インターフェイスを実装します。

```csharp
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);
    // ...
}
```

ただし、コードが、規則を適用する優れた方法として、特定の集計を対象とするリポジトリを使用している明示的なので、汎用的なリポジトリの種類を実装すること、1 つの集計に各リポジトリを関連付ける必要があります。 簡単に行えます IRepository 基本インターフェイスで、次のコードのように、そのジェネリックを実装することで。

```csharp
  public interface IRepository<T> where T : IAggregateRoot
```

### <a name="the-repository-pattern-makes-it-easier-to-test-your-application-logic"></a>リポジトリ パターンしやすく、アプリケーション ロジックをテストするには

リポジトリ パターンでは、単体テストでアプリケーションを簡単にテストすることができます。 単体テストのみをテスト コード、インフラストラクチャではなく、リポジトリの抽象化によりその目的を達成しやすくために注意してください。

定義して配置リポジトリ インターフェイス ドメイン モデル レイヤーにおいて、アプリケーション レイヤー (マイクロたとえばに、Web API サービス) が、インフラストラクチャ レイヤーに直接依存しないようにがあることお勧め述べたように、前のセクションで、実際のリポジトリ クラスを実装します。 これを行うと、依存関係の挿入を使用して、Web api コント ローラーで、データベースからデータではなく偽のデータを返すモック リポジトリを実装できます。 分離アプローチでは、作成することができ、実行の単位をテストすることは、データベースへの接続を必要とせず、アプリケーションのロジックだけをテストできます。

データベースへの接続が失敗する可能性し、さらに、データベースに対して数百台のテストを実行しているが、不適切な 2 つの理由。 最初に、テスト数が多いため、多くの時間がかかることができます。 次に、データベースのレコードは、変更し、一貫性のある可能性がありますいないできるように、テストの結果に影響します。 テスト データベースに対してはなく、単体テストとの統合をテストします。 高速で実行されている多くの単体テストが必要ですが、データベースに対して以下の統合をテストします。

単体テストの関心の分離の観点から、ロジックは、メモリ内のドメイン エンティティで動作します。 リポジトリのクラスが配信されるものと見なします。 ロジックは、ドメイン エンティティを変更すると、リポジトリはストア クラスに正しく想定しています。 ここでの重要なポイントでは、ドメイン モデルとそのドメイン ロジックに対して単体テストを作成します。 集計のルートは、DDD でメイン整合性境界です。

### <a name="the-difference-between-the-repository-pattern-and-the-legacy-data-access-class-dal-class-pattern"></a>リポジトリ パターンと、従来のデータ アクセス クラス (DAL) パターンの違い

データ アクセス オブジェクトは、記憶域に対するデータ アクセスおよび永続化操作を直接実行します。 (EF DbContext を使用する場合) と同じ作業オブジェクトが、これらの更新プログラムの単位のメモリで実行する操作とデータはすぐに実行されませんリポジトリ マークします。

作業の単位は、単一のトランザクションとして一種で、複数の挿入、更新、または削除操作に呼ばれます。 簡単に言えば、特定のユーザーの操作 (たとえば、web サイトに登録) のすべての insert、update、および削除トランザクションが処理されることで 1 つのトランザクションを意味します。 これは、対話方法で複数のデータベース トランザクションを処理するよりも効率的です。

コマンドのコードをアプリケーション層からときに、これら複数の永続化操作を 1 つのアクションで後で実行されます。 に基づいて決定された実際のデータベースの記憶域にメモリ内の変更の適用については、通常、[作業単位パターン](http://martinfowler.com/eaaCatalog/unitOfWork.html)です。 EF には、作業単位のパターンは、DBContext として実装されます。

多くの場合、このパターン、または記憶域に対する操作を適用する方法アプリケーションのパフォーマンスを向上させるでき不一致の可能性を低減できます。 意図したすべての操作は 1 つのトランザクションの一部としてコミットされるので、データベース テーブル内のブロック トランザクションが低くなります。 これは、データベースに対して多数の単独の操作を実行するシステムと比べて効率的です。 このため、選択した ORM は多くの小規模で別のトランザクションの実行ではなく、同じトランザクション内でいくつかの更新アクションをグループ化して、データベースに対して実行を最適化することになります。

### <a name="repositories-should-not-be-mandatory"></a>リポジトリを固定することはできません。

カスタム リポジトリは、前に挙げたの理由により便利ですお eShopOnContainers で順序付けマイクロ サービスの実行方法。 ただし、DDD 設計の実装も一般に .NET での開発の不可欠なパターンではありません。

インスタンスの Jimmy Bogard、このガイドでは、直接フィードバックを提供するときに、次と言います。

これが最も大きなフィードバック、可能性があります。 私は本当にない、リポジトリのファン基になる永続化メカニズムの重要な詳細を非表示にするために主にします。 これは、理由進め MediatR のコマンドをすぎます。 永続レイヤーのすべての機能を使用して my 集計ルートにそのすべてのドメインの動作をプッシュします。 自分のリポジトリを模擬表示したくない通常 – が必要な統合がある実際の作業をテストします。 実際にありませんでしたリポジトリが必要かどうかを意図したもので CQRS を移動します。

リポジトリを役に立つことが、集計のパターンとリッチ ドメイン モデルはその方法で、DDD にとって重要ではないということを承認します。 したがって、リポジトリ パターンを使用するか、わかるに合わせてください。

#### <a name="additional-resources"></a>その他の技術情報

##### <a name="the-repository-pattern"></a>リポジトリ パターン

-   **Edward Hieatt および Rob me です。リポジトリ パターン。** 
     [ *http://martinfowler.com/eaaCatalog/repository.html*](http://martinfowler.com/eaaCatalog/repository.html)

-   **リポジトリ パターン**
    [*https://msdn.microsoft.com/en-us/library/ff649690.aspx*](https://msdn.microsoft.com/en-us/library/ff649690.aspx)

-   **リポジトリ パターン: データ持続性の抽象化**
    [*http://deviq.com/repository-pattern/*](http://deviq.com/repository-pattern/)

-   **Eric Evans。ドメインに基づく設計: は Tackling Complexity in the Heart of Software です。** (予約以外の場合は、リポジトリ パターンの詳細についてにが含まれています)[ *https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

##### <a name="unit-of-work-pattern"></a>作業のパターンの単位

-   **Martin Fowler。作業のパターンの単位。** 
     [ *http://martinfowler.com/eaaCatalog/unitOfWork.html*](http://martinfowler.com/eaaCatalog/unitOfWork.html)

<!-- -->

-   **ASP.NET MVC アプリケーションのリポジトリと作業パターンの単位を実装する**
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)


>[!div class="step-by-step"]
[前](ドメインのイベントの設計の implementation.md) [次へ] (infrastructure-persistence-layer-implemenation-entity-framework-core.md)
