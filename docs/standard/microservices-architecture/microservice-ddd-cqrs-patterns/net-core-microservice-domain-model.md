---
title: ".NET Core のマイクロ サービス ドメイン モデルを実装します。"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |.NET Core のマイクロ サービス ドメイン モデルを実装します。"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 26c480a82ad7bb806734decebdfbe5b4a07998e6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-a-microservice-domain-model-with-net-core"></a>.NET Core のマイクロ サービス ドメイン モデルを実装します。 

前のセクションで、基本的なデザインの原則とドメイン モデルをデザインするためのパターンがについて説明します。 では、.NET Core を使用してドメイン モデルを実装する方法を検討する時間 (plain C\#コード) と EF コアです。 ドメイン モデルは単に、コードから構成することに注意してください。 EF の EF 中核となるモデルの要件がない実際の依存関係だけがあります。 ドメイン モデルのハード依存関係または EF コアまたはその他の任意の ORM への参照をことはできません。

## <a name="domain-model-structure-in-a-custom-net-standard-library"></a>カスタム .NET 標準ライブラリ内のドメイン モデルの構造

EShopOnContainers 参照アプリケーションの使用フォルダー組織では、アプリケーションの DDD モデルについて説明します。 別のフォルダーの組織は、アプリケーションに対して行われた設計の選択肢をより明確に通信することがあります。 図 9-10 がわかるように順序ドメイン モデルでは 2 つの集計、順序集計および buyer 集計。 各集計は、集計も (集計ルートまたはルート エンティティ) は、1 つのドメイン エンティティで構成する必要でしたが、ドメイン エンティティおよび値オブジェクトのグループです。

![](./media/image11.png)

**図 9-10**です。 EShopOnContainers で順序付けマイクロ サービスのドメイン モデルの構造

さらに、ドメイン モデル レイヤーには、ドメイン モデルのインフラストラクチャの要件は、リポジトリ コントラクト (インターフェイス) が含まれています。 つまり、これらのインターフェイスがどのようなリポジトリ インフラストラクチャ レイヤーを実装する必要がありますを express とどのようにします。 すべてのユーザーをドメイン モデル層がない「感染」API または Entity Framework などのインフラストラクチャ テクノロジからのクラスによってように、インフラストラクチャ レイヤー ライブラリで、ドメイン モデル レイヤーの外側に配置リポジトリの実装が重要です。

表示することも、 [SeedWork](https://martinfowler.com/bliki/Seedwork.html)ドメイン エンティティと値のベースとして使用できるカスタムの基本クラスが含まれているフォルダーのオブジェクト、ため、各ドメインのオブジェクト クラスで、冗長なコードはありません。

## <a name="structuring-aggregates-in-a-custom-net-standard-library"></a>カスタム .NET 標準ライブラリでの集計の構築

集計は、トランザクションの一貫性を一致するように一緒にグループ化されたドメイン オブジェクトのクラスターを指します。 これらのオブジェクトには、さらに、追加の値のオブジェクト (一方が集計ルートまたはルート エンティティ) のエンティティのインスタンス可能性があります。

トランザクションの一貫性は、集計は確実に一貫性があり、ビジネス アクションの末尾に最新の状態を意味します。 たとえば、図 9-11 ようにマイクロ サービス ドメイン モデルを順序付け eShopOnContainers から注文集計が構成されます。

![](./media/image12.png)

**図 9-11**です。 Visual Studio ソリューションで集計の順序

Aggregate フォルダー内のすべてのファイルを開く、表示できますエンティティまたは値のオブジェクトと同様に、インターフェイスまたはカスタムの基本クラスとしてマークされている方法で実装されている、 [Seedwork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork)フォルダーです。

## <a name="implementing-domain-entities-as-poco-classes"></a>POCO クラスとして実装のドメイン エンティティ

.NET のドメイン モデルを実装するには、ドメイン エンティティを実装する POCO クラスを作成します。 次の例では、エンティティおよび集計ルートとしても Order クラスが定義されています。 Order クラスは、エンティティの基本クラスから派生する、ので、エンティティに関連する一般的なコードを再利用することができます。 これらの基本クラスとインターフェイスがで定義されているユーザーがドメイン モデル プロジェクトので、コード、EF と同様に、ORM からインフラストラクチャ コードではなく念頭に置いてください。

```csharp
// COMPATIBLE WITH ENTITY FRAMEWORK CORE 1.0
// Entity is a custom base class with the ID
public class Order : Entity, IAggregateRoot
{
    public int BuyerId { get; private set; }
    public DateTime OrderDate { get; private set; }
    public int StatusId { get; private set; }
    public ICollection<OrderItem> OrderItems { get; private set; }
    public Address ShippingAddress { get; private set; }
    public int PaymentId { get; private set; }
    protected Order() { } //Design constraint needed only by EF Core
    public Order(int buyerId, int paymentId)
    {
        BuyerId = buyerId;
        PaymentId = paymentId;
        StatusId = OrderStatus.InProcess.Id;
        OrderDate = DateTime.UtcNow;
        OrderItems = new List<OrderItem>();
    }

    public void AddOrderItem(productName,
        pictureUrl,
        unitPrice,
        discount,
        units)
    {
        //...
        // Domain rules/logic for adding the OrderItem to the order
        // ...
        OrderItem item = new OrderItem(this.Id, ProductId, productName,
            pictureUrl, unitPrice, discount, units);
  
        OrderItems.Add(item);
    }
    // ...
    // Additional methods with domain rules/logic related to the Order aggregate
    // ...
}
```

これは、POCO クラスとして実装されているドメイン エンティティであることに注意してくださいに重要です。 Entity Framework のコアの直接的な依存関係またはその他のインフラストラクチャ フレームワークはありません。 この実装は必要があります、C だけ\#ドメイン モデルを実装するコードです。

さらに、クラスは、IAggregateRoot をという名前のインターフェイスで装飾されています。 そのインターフェイスとも呼ばれる、空のインターフェイスは、*マーカー インターフェイスに*、それがあることを示すこのエンティティ クラスも集計ルートにだけ使用します。

マーカー インターフェイスには、アンチ パターンとしてと見なされることただし、そのインターフェイスが変化し続ける可能性がある場合は特に、クラスをマークする明確な方法ではもです。 属性は、マーカーの他の選択肢になる可能性がありますが、クラス上にある、集計 attribute マーカーを設定する代わりに、IAggregate インターフェイスの横にある基本クラス (エンティティ) を参照する方が手軽です。 いずれの場合、基本設定の metter であります。

整合性に関連するほとんどのコードと、集計のエンティティのビジネス ルールを Order 集計ルート クラス (たとえば、AddOrderItem の集計に OrderItem オブジェクトを追加する場合) 内のメソッドとして実装する集計ルートを持つ. 作成または個別にも直接に OrderItems オブジェクトを更新する必要がありますされません。AggregateRoot クラスには、コントロールとその子エンティティに対して更新操作の一貫性を維持する必要があります。

たとえば、する必要があります*いない*コマンド ハンドラー メソッドまたはアプリケーション レイヤーのクラスから次の操作します。

```csharp
// WRONG ACCORDING TO DDD PATTERNS – CODE AT THE APPLICATION LAYER OR
// COMMAND HANDLERS
// Code in command handler methods or Web API controllers
//... (WRONG) Some code with business logic out of the domain classes ...
OrderItem myNewOrderItem = new OrderItem(orderId, productId, productName,
    pictureUrl, unitPrice, discount, units);

//... (WRONG) Accessing the OrderItems colletion directly from the application layer // or command handlers
myOrder.OrderItems.Add(myNewOrderItem);
//...
```

この例では、Add メソッドは OrderItems コレクションに直接アクセスできる、データを追加する操作のみです。 そのため、ドメイン ロジック、ルール、または検証のほとんどに関連するアプリケーション層 (コマンド ハンドラーおよび Web API コント ローラー) は、子エンティティと操作に分散することです。

集計のルートを移動する場合、集計のルートは、不変条件や、その有効性の一貫性を保証できません。 最終的に整然としたプログラムまたはトランザクション スクリプト コードがあります。

DDD パターンに従うと、エンティティには、すべてのエンティティのプロパティでパブリック setter がない必要です。 エンティティの変更は、エンティティで実行している変更に関する明確なユビキタス言語を持つ明示的なメソッドによって推進する必要があります。

さらに、(、注文項目など)、エンティティ内にコレクションが読み取り専用プロパティをする必要があります (されましたメソッドは後で説明します)。 集計のルート クラスのメソッドや子エンティティ メソッド内からのみ更新することができます。

順序集計ルート用のコードに示すように、すべての set アクセス操作子する必要がありますプライベートまたは読み取り専用には、少なくとも外部で、エンティティのデータまたはその子エンティティに対して操作が、そのエンティティ クラスのメソッドによって実行されるがあるできるようにします。 これにより、トランザクション スクリプト コードを実装する代わりに制御およびオブジェクト指向の方法で一貫性が維持されます。

次のコード スニペットは、注文の集計に OrderItem オブジェクトを追加するタスクを記述する適切な方法を示しています。

```csharp
// RIGHT ACCORDING TO DDD--CODE AT THE APPLICATION LAYER OR COMMAND HANDLERS
// The code in command handlers or WebAPI controllers, related only to application stuff
// There is NO code here related to OrderItem object’s business logic
myOrder.AddOrderItem(productId, productName, pictureUrl, unitPrice, discount, units);

// The code related to OrderItem params validations or domain rules should
// be WITHIN the AddOrderItem method.

//...
```

このスニペットでほとんどの検証または OrderItem オブジェクトの作成に関連するロジックなります順序集計ルートの制御下-AddOrderItem メソッドで — 特に検証とロジックに関連するその他の要素、集計します。 たとえば、AddOrderItem が複数の呼び出しの結果として同じ製品品目をする可能性があります。 そのメソッドでは、製品のアイテムは検証し、いくつかの単位である単一の OrderItem オブジェクトに同じ製品品目を統合するでした。 また、さまざまな割引金額があるが、製品 ID は同じ場合に、割引率が高いを適用可能性がありますはします。 この原則は、OrderItem オブジェクトの他のドメイン ロジックを適用します。

さらに、新しい OrderItem(params) 操作も管理対象し、する注文集計ルートから AddOrderItem メソッドによって実行されます。 そのため、ほとんどのロジックおよび検証に関連する操作 (特に他の子エンティティ間の一貫性に影響を与えるもの) が、集計のルート内の 1 つの場所に含まれます。 集計のルート パターンの最終的な目的です。

Entity Framework 1.1 を使用して、DDD エンティティより表現できることができるエンティティ フレームワークのコア 1.1 の新機能の 1 つが[フィールドへのマッピング](https://docs.microsoft.com/ef/core/modeling/backing-field)プロパティだけでなくです。 これは、機能は、子エンティティや値のオブジェクトのコレクションを保護するときに便利です。 この拡張機能プロパティの代わりに単純なプライベート フィールドを使用することができ、パブリック メソッドのフィールド コレクションに、更新プログラムを実装し、されましたメソッドを介して読み取り専用アクセスを提供することができます。

DDD では、任意の不変性とデータの整合性を制御するために、エンティティ (または、コンス トラクター) メソッドによってのみ、エンティティを更新する、ためのプロパティが定義されている get アクセサーでのみです。 プロパティは、プライベート フィールドでサポートされます。 プライベート メンバーは、クラス内からのみアクセスできます。 ただし、ある 1 つの例外: EF コアは、これらのフィールドも設定する必要があります。

```csharp
// ENTITY FRAMEWORK CORE 1.1 OR LATER
// Entity is a custom base class with the ID
public class Order : Entity, IAggregateRoot
{
    // DDD Patterns comment
    // Using private fields, allowed since EF Core 1.1, is a much better
    // encapsulation aligned with DDD aggregates and domain entities (instead of
    // properties and property collections)
    private bool _someOrderInternalState;
    private DateTime _orderDate;
    public Address Address { get; private set; }
    public Buyer Buyer { get; private set; }
    private int _buyerId;
    public OrderStatus OrderStatus { get; private set; }
    private int _orderStatusId;

    // DDD patterns comment
    // Using a private collection field is better for DDD aggregate encapsulation.
    // OrderItem objects cannot be added from outside the aggregate root
    // directly to the collection, but only through the
    // OrderAggrergateRoot.AddOrderItem method, which includes behavior.
    private readonly List<OrderItem> _orderItems;
    public IEnumerable<OrderItem> OrderItems => _orderItems.AsReadOnly();
    // Using List<>.AsReadOnly()
    // This will create a read-only wrapper around the private list so it is
    // protected against external updates. It's much cheaper than .ToList(),
    // because it will not have to copy all items in a new collection.
    // (Just one heap alloc for the wrapper instance)
    // https://msdn.microsoft.com/en-us/library/e78dcd75(v=vs.110).aspx
    public PaymentMethod PaymentMethod { get; private set; }
    private int _paymentMethodId;

    protected Order() { }

    public Order(int buyerId, int paymentMethodId, Address address)
    {
        _orderItems = new List<OrderItem>();
        _buyerId = buyerId;
        _paymentMethodId = paymentMethodId;
        _orderStatusId = OrderStatus.InProcess.Id;
        _orderDate = DateTime.UtcNow;
        Address = address;
    }

    // DDD patterns comment
    // The Order aggregate root method AddOrderitem() should be the only way
    // to add items to the Order object, so that any behavior (discounts, etc.)
    // and validations are controlled by the aggregate root in order to
    // maintain consistency within the whole aggregate.
    public void AddOrderItem(int productId, string productName, decimal unitPrice,
        decimal discount, string pictureUrl, int units = 1)
    {
        // ...
        // Domain rules/logic here for adding OrderItem objects to the order
        // ...
        OrderItem item = new OrderItem(this.Id, productId, productName,
            pictureUrl, unitPrice, discount, units);
        OrderItems.Add(item);
    }

    // ...
    // Additional methods with domain rules/logic related to the Order aggregate
    // ...
}
```

### <a name="mapping-properties-with-only-get-accessors-to-the-fields-in-the-database-table"></a>のみとマッピングのプロパティの get アクセサーのフィールドに、データベース テーブル

プロパティをデータベース テーブルの列にマップはなく、ドメイン責任インフラストラクチャと持続性層の一部です。 記述されてこのだけエンティティをモデル化する方法に関連する EF 1.1 の新機能に注意してください。 このトピックの詳細については、インフラストラクチャおよび永続化のセクションで説明します。

データベース テーブルの実際のフィールドに get アクセス操作子でのみ定義されているプロパティをマップする必要があります。 DbContext 内の EF 1.0 を使用する場合。 これは PropertyBuilder クラスの HasField メソッドを使用して行われます。

### <a name="mapping-fields-without-properties"></a>プロパティのないフィールドのマッピング

列フィールドをマップする EF コア 1.1 の新機能を使用可能であればもプロパティを使用しないようにします。 代わりに、フィールドに、テーブルの列にのみマップできます。 この一般的なユース ケースは、エンティティの外部からアクセスする必要はありませんを内部の状態のプライベート フィールドです。

たとえば、前のコード例で、 \_someOrderInternalState フィールドには、setter または getter 用に関連するプロパティがありません。 そのフィールドは注文のビジネス ロジック内で計算され、注文の方法を使用するもデータベースに保存される必要があります。 そのため、EF 1.1 では、データベース内の列に関連するプロパティを持たないフィールドをマップする方法です。 これで説明しても、[インフラストラクチャ レイヤー](#the-infrastructure-layer)このガイドの「します。

### <a name="additional-resources"></a>その他の技術情報

-   **Vaughn Vernon。DDD および Entity Framework では集計をモデリングです。** これは*いない*エンティティ フレームワークのコアです。
    [*https://vaughnvernon.co/?p=879*](https://vaughnvernon.co/?p=879)

-   **Julie Lerman です。ドメイン ベースのデザインのコーディング: データに重点を置いた開発者用ヒント**
    [*https://msdn.microsoft.com/en-us/magazine/dn342868.aspx*](https://msdn.microsoft.com/en-us/magazine/dn342868.aspx)

-   **Udi Dahan です。ドメイン モデルが完全に作成する方法にカプセル化された**
    [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)


>[!div class="step-by-step"]
[前](マイクロ サービスのドメイン-model.md) [次へ] (seedwork-domain-model-base-classes-interfaces.md)
