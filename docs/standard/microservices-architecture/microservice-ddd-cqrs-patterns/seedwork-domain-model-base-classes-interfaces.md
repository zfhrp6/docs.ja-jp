---
title: "Seedwork (ドメイン モデルの再利用可能な基底クラスとインターフェイス)"
description: "コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | Seedwork (ドメイン モデルの再利用可能な基底クラスとインターフェイス)"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: aba336676a558f50a2669eb3ca096effb8387916
ms.sourcegitcommit: 91691981897cf8451033cb01071d8f5d94017f97
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2018
---
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a><span data-ttu-id="635ae-104">Seedwork (ドメイン モデルの再利用可能な基底クラスとインターフェイス)</span><span class="sxs-lookup"><span data-stu-id="635ae-104">Seedwork (reusable base classes and interfaces for your domain model)</span></span>

<span data-ttu-id="635ae-105">ソリューション フォルダーには、*SeedWork* フォルダーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="635ae-105">The solution folder contains a *SeedWork* folder.</span></span> <span data-ttu-id="635ae-106">*SeedWork* フォルダー内にあるカスタム基底クラスは、ドメイン エンティティおよび値オブジェクトの基礎として使用できます。</span><span class="sxs-lookup"><span data-stu-id="635ae-106">The *SeedWork* folder contains custom base classes that you can use as a base for your domain entities and value objects.</span></span> <span data-ttu-id="635ae-107">これらの基底クラスを使用すると、各ドメインのオブジェクト クラスで冗長なコードがなくなります。</span><span class="sxs-lookup"><span data-stu-id="635ae-107">Use these base classes so you do not have redundant code in each domain’s object class.</span></span> <span data-ttu-id="635ae-108">これらのタイプのクラス用のフォルダーは、*Framework* のような名前ではなく、*SeedWork* という名前になっています。</span><span class="sxs-lookup"><span data-stu-id="635ae-108">The folder for these types of classes is called *SeedWork* and not something like *Framework*.</span></span> <span data-ttu-id="635ae-109">*SeedWork* という名前になっているのは、このフォルダーには再利用可能なクラスのほんの一部しか含まれておらず、実際にはフレームワークと見なすことができないためです。</span><span class="sxs-lookup"><span data-stu-id="635ae-109">It's called *SeedWork* because the folder contains just a small subset of reusable classes which cannot really be considered a framework.</span></span> <span data-ttu-id="635ae-110">*Seedwork* は、[Michael Feathers](http://www.artima.com/forums/flat.jsp?forum=106&thread=8826) が発表し、[Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) が普及させた用語ですが、Common や SharedKernel といった名前で呼ばれる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="635ae-110">*Seedwork* is a term introduced by [Michael Feathers](http://www.artima.com/forums/flat.jsp?forum=106&thread=8826) and popularized by [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) but you could also name that folder Common, SharedKernel, or similar.</span></span>

<span data-ttu-id="635ae-111">図 9-12 は、注文マイクロサービスのドメイン モデルの SeedWork を構成するクラスを示しています。</span><span class="sxs-lookup"><span data-stu-id="635ae-111">Figure 9-12 shows the classes that form the seedwork of the domain model in the ordering microservice.</span></span> <span data-ttu-id="635ae-112">カスタム基底クラス (Entity、ValueObject、Enumeration など) とインターフェイスがいくつか含まれています。</span><span class="sxs-lookup"><span data-stu-id="635ae-112">It has a few custom base classes like Entity, ValueObject, and Enumeration, plus a few interfaces.</span></span> <span data-ttu-id="635ae-113">これらのインターフェイス (IRepository と IUnitOfWork) は、実装する必要があるものをインフラストラクチャ レイヤーに通知します。</span><span class="sxs-lookup"><span data-stu-id="635ae-113">These interfaces (IRepository and IUnitOfWork) inform the infrastructure layer about what needs to be implemented.</span></span> <span data-ttu-id="635ae-114">また、これらのインターフェイスは、アプリケーション レイヤーから依存関係の挿入を通じて使用されます。</span><span class="sxs-lookup"><span data-stu-id="635ae-114">Those interfaces are also used through Dependency Injection from the application layer.</span></span>

![](./media/image13.PNG)

<span data-ttu-id="635ae-115">**図 9-12**.</span><span class="sxs-lookup"><span data-stu-id="635ae-115">**Figure 9-12**.</span></span> <span data-ttu-id="635ae-116">ドメイン モデル "SeedWork" の基底クラスとインターフェイスのサンプル セット</span><span class="sxs-lookup"><span data-stu-id="635ae-116">A sample set of domain model “seedwork" base classes and interfaces</span></span>

<span data-ttu-id="635ae-117">これは、コピーと貼り付けによって再利用するタイプのもので、多くの開発者によってプロジェクト間で共有されます。正式なフレームワークではありません。</span><span class="sxs-lookup"><span data-stu-id="635ae-117">This is the type of copy and paste reuse that many developers share between projects, not a formal framework.</span></span> <span data-ttu-id="635ae-118">SeedWork は、どのレイヤーやライブラリでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="635ae-118">You can have seedworks in any layer or library.</span></span> <span data-ttu-id="635ae-119">ただし、クラスとインターフェイスのセットが十分に大きくなったら、単一のクラス ライブラリを作成するのがよいでしょう。</span><span class="sxs-lookup"><span data-stu-id="635ae-119">However, if the set of classes and interfaces gets big enough, you might want to create a single class library.</span></span>

## <a name="the-custom-entity-base-class"></a><span data-ttu-id="635ae-120">カスタム Entity 基底クラス</span><span class="sxs-lookup"><span data-stu-id="635ae-120">The custom Entity base class</span></span>

<span data-ttu-id="635ae-121">次のコードは、Entity 基底クラスの例です。このクラスでは、任意のドメイン エンティティ (エンティティ ID、[等値演算子](/cpp/cpp/equality-operators-equal-equal-and-exclpt-equal)、エンティティごとのドメイン イベント リストなど) が同様の方法で使用できるコードを配置できます。</span><span class="sxs-lookup"><span data-stu-id="635ae-121">The following code is an example of an Entity base class where you can place code that can be used the same way by any domain entity, such as the entity ID, [equality operators](/cpp/cpp/equality-operators-equal-equal-and-exclpt-equal), a domain event list per entity, etc.</span></span>

```csharp
// COMPATIBLE WITH ENTITY FRAMEWORK CORE (1.1 and later)
public abstract class Entity
{
    int? _requestedHashCode;
    int _Id;    
    private List<INotification> _domainEvents;
    public virtual int Id 
    {
        get
        {
            return _Id;
        }
        protected set
        {
            _Id = value;
        }
    }

    public List<INotification> DomainEvents => _domainEvents;        
    public void AddDomainEvent(INotification eventItem)
    {
        _domainEvents = _domainEvents ?? new List<INotification>();
        _domainEvents.Add(eventItem);
    }
    public void RemoveDomainEvent(INotification eventItem)
    {
        if (_domainEvents is null) return;
        _domainEvents.Remove(eventItem);
    }

    public bool IsTransient()
    {
        return this.Id == default(Int32);
    }

    public override bool Equals(object obj)
    {
        if (obj == null || !(obj is Entity))
            return false;
        if (Object.ReferenceEquals(this, obj))
            return true;
        if (this.GetType() != obj.GetType())
            return false;
        Entity item = (Entity)obj;
        if (item.IsTransient() || this.IsTransient())
            return false;
        else
            return item.Id == this.Id;
    }

    public override int GetHashCode()
    {
        if (!IsTransient())
        {
            if (!_requestedHashCode.HasValue)
                _requestedHashCode = this.Id.GetHashCode() ^ 31; 
            // XOR for random distribution. See:
            // http://blogs.msdn.com/b/ericlippert/archive/2011/02/28/guidelines-and-rules-for-gethashcode.aspx
            return _requestedHashCode.Value;
        }
        else
            return base.GetHashCode();
    }
    public static bool operator ==(Entity left, Entity right)
    {
        if (Object.Equals(left, null))
            return (Object.Equals(right, null)) ? true : false;
        else
            return left.Equals(right);
    }
    public static bool operator !=(Entity left, Entity right)
    {
        return !(left == right);
    }
}
```

<span data-ttu-id="635ae-122">エンティティごとのドメイン イベント リストを使用する以前のコードについては、次のセクションでドメイン イベントを取り上げるときに説明します。</span><span class="sxs-lookup"><span data-stu-id="635ae-122">The previous code using a domain event list per entity will be explained in the next sections when focusing on domain events.</span></span> 

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a><span data-ttu-id="635ae-123">ドメイン モデル レイヤーのリポジトリ コントラクト (インターフェイス)</span><span class="sxs-lookup"><span data-stu-id="635ae-123">Repository contracts (interfaces) in the domain model layer</span></span>

<span data-ttu-id="635ae-124">リポジトリ コントラクトは、各集計に使用されるリポジトリのコントラクト要件を示すシンプルな .NET インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="635ae-124">Repository contracts are simply .NET interfaces that express the contract requirements of the repositories to be used for each aggregate.</span></span> 

<span data-ttu-id="635ae-125">リポジトリ自体と EF コア コード、または他の任意のインフラストラクチャの依存関係やコード (Linq や SQL など) は、ドメイン モデル内に実装してはなりません。リポジトリは、ユーザー定義のインターフェイスのみを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="635ae-125">The repositories themselves, with EF Core code or any other infrastructure dependencies and code (Linq, SQL, etc.), must not be implemented within the domain model; the repositories should only implement the interfaces you define.</span></span> 

<span data-ttu-id="635ae-126">この手法 (リポジトリ インターフェイスをドメイン モデル レイヤーに配置する手法) に関連するパターンが、インターフェイスの分離 パターンです。</span><span class="sxs-lookup"><span data-stu-id="635ae-126">A pattern related to this practice (placing the repository interfaces in the domain model layer) is the Separated Interface pattern.</span></span> <span data-ttu-id="635ae-127">Martin Fowler は、次のように[説明](http://www.martinfowler.com/eaaCatalog/separatedInterface.html)しています。"インターフェイスの分離を使用して、あるインターフェイスをあるパッケージに定義します。ただし、その実装は、別のパッケージで行います。</span><span class="sxs-lookup"><span data-stu-id="635ae-127">As [explained](http://www.martinfowler.com/eaaCatalog/separatedInterface.html) by Martin Fowler, “Use Separated Interface to define an interface in one package but implement it in another.</span></span> <span data-ttu-id="635ae-128">これにより、このインターフェイスへの依存関係が必要なクライアントは、実装を全く意識せずにすむようになります。"</span><span class="sxs-lookup"><span data-stu-id="635ae-128">This way a client that needs the dependency to the interface can be completely unaware of the implementation.”</span></span>

<span data-ttu-id="635ae-129">インターフェイスの分離パターンに従うと、アプリケーション レイヤー (この場合はマイクロサービスの Web API プロジェクト) は、ドメイン モデルで定義された要件に対する依存関係を持つことができます。ただし、インフラストラクチャ/ 永続化レイヤーに対する直接の依存関係を持つことはできません。</span><span class="sxs-lookup"><span data-stu-id="635ae-129">Following the Separated Interface pattern enables the application layer (in this case, the Web API project for the microservice) to have a dependency on the requirements defined in the domain model, but not a direct dependency to the infrastructure/persistence layer.</span></span> <span data-ttu-id="635ae-130">また、依存関係の挿入を使用すると、リポジトリを使用してインフラストラクチャ/永続化レイヤーに実装された実装を分離できます。</span><span class="sxs-lookup"><span data-stu-id="635ae-130">In addition, you can use Dependency Injection to isolate the implementation, which is implemented in the infrastructure/ persistence layer using repositories.</span></span>

<span data-ttu-id="635ae-131">たとえば、IOrderRepository インターフェイスを使用する次の例では、OrderRepository クラスがインフラストラクチャ レイヤーで実装する必要のある操作が定義されています。</span><span class="sxs-lookup"><span data-stu-id="635ae-131">For example, the following example with the IOrderRepository interface defines what operations the OrderRepository class will need to implement at the infrastructure layer.</span></span> <span data-ttu-id="635ae-132">アプリケーションの現在の実装では、簡略化された CQRS アプローチに従ってクエリが分割されているため、コードは、データベースに注文を追加するか、またはデータベースの注文を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="635ae-132">In the current implementation of the application, the code just needs to add or update orders to the database, since queries are split following the simplified CQRS approach.</span></span>

```csharp
// Defined at IOrderRepository.cs
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);
        
    void Update(Order order);

    Task<Order> GetAsync(int orderId);
}

// Defined at IRepository.cs (Part of the Domain Seedwork)
public interface IRepository<T> where T : IAggregateRoot
{
    IUnitOfWork UnitOfWork { get; }
}
```

## <a name="additional-resources"></a><span data-ttu-id="635ae-133">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="635ae-133">Additional resources</span></span>

-   <span data-ttu-id="635ae-134">**Martin Fowler。「Separated Interface」(インターフェイスの分離)。**
    [*http://www.martinfowler.com/eaaCatalog/separatedInterface.html*](http://www.martinfowler.com/eaaCatalog/separatedInterface.html)</span><span class="sxs-lookup"><span data-stu-id="635ae-134">**Martin Fowler. Separated Interface.**
[*http://www.martinfowler.com/eaaCatalog/separatedInterface.html*](http://www.martinfowler.com/eaaCatalog/separatedInterface.html)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="635ae-135">[前] (net-core-microservice-domain-model.md) [次] (implement-value-objects.md)</span><span class="sxs-lookup"><span data-stu-id="635ae-135">[Previous] (net-core-microservice-domain-model.md) [Next] (implement-value-objects.md)</span></span>
