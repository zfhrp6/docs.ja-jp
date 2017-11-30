---
title: "Seedwork (再利用可能な基本クラスと、ドメイン モデルのインターフェイス)"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |Seedwork (再利用可能な基本クラスと、ドメイン モデルのインターフェイス)"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 17602d94ea167997389a77f0d2358326258a8219
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a><span data-ttu-id="2b4e0-104">Seedwork (再利用可能な基本クラスと、ドメイン モデルのインターフェイス)</span><span class="sxs-lookup"><span data-stu-id="2b4e0-104">Seedwork (reusable base classes and interfaces for your domain model)</span></span>

<span data-ttu-id="2b4e0-105">ソリューション フォルダーに含まれる、 *SeedWork*フォルダーです。</span><span class="sxs-lookup"><span data-stu-id="2b4e0-105">The solution folder contains a *SeedWork* folder.</span></span> <span data-ttu-id="2b4e0-106">*SeedWork*フォルダーには、ドメインのエンティティおよび値オブジェクトをベースとして使用できるカスタムの基本クラスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2b4e0-106">The *SeedWork* folder contains custom base classes that you can use as a base for your domain entities and value objects.</span></span> <span data-ttu-id="2b4e0-107">各ドメインのオブジェクト クラスで、冗長なコードはありませんので、これらの基本クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="2b4e0-107">Use these base classes so you do not have redundant code in each domain’s object class.</span></span> <span data-ttu-id="2b4e0-108">これらの型クラスのフォルダーと呼びます*SeedWork*などのメカニズムではありませんし*Framework*です。</span><span class="sxs-lookup"><span data-stu-id="2b4e0-108">The folder for these types of classes is called *SeedWork* and not something like *Framework*.</span></span> <span data-ttu-id="2b4e0-109">呼び出された*SeedWork*フォルダーには、フレームワークは見なされません本当に再利用可能なクラスの小さなサブセットのみが含まれているためです。</span><span class="sxs-lookup"><span data-stu-id="2b4e0-109">It's called *SeedWork* because the folder contains just a small subset of reusable classes which cannot really be considered a framework.</span></span> <span data-ttu-id="2b4e0-110">*Seedwork*用語によって導入[Michael の受信可能方向](http://www.artima.com/forums/flat.jsp?forum=106&thread=8826)が増幅し、 [Martin ファウラー](https://martinfowler.com/bliki/Seedwork.html)共通、SharedKernel、フォルダーの名前もでしたが、または類似します。</span><span class="sxs-lookup"><span data-stu-id="2b4e0-110">*Seedwork* is a term introduced by [Michael Feathers](http://www.artima.com/forums/flat.jsp?forum=106&thread=8826) and popularized by [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) but you could also name that folder Common, SharedKernel, or similar.</span></span>

<span data-ttu-id="2b4e0-111">図 9-12 では、順序付けのマイクロ サービスにドメイン モデルの seedwork を形成するクラスを示します。</span><span class="sxs-lookup"><span data-stu-id="2b4e0-111">Figure 9-12 shows the classes that form the seedwork of the domain model in the ordering microservice.</span></span> <span data-ttu-id="2b4e0-112">エンティティ、ValueObject、および列挙体と同様に、いくつかのカスタムの基本クラスとインターフェイスのいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="2b4e0-112">It has a few custom base classes like Entity, ValueObject, and Enumeration, plus a few interfaces.</span></span> <span data-ttu-id="2b4e0-113">(IRepository および IUnitOfWork) これらのインターフェイスを実装する必要のあるについて、インフラストラクチャ レイヤーに通知します。</span><span class="sxs-lookup"><span data-stu-id="2b4e0-113">These interfaces (IRepository and IUnitOfWork) inform the infrastructure layer about what needs to be implemented.</span></span> <span data-ttu-id="2b4e0-114">これらのインターフェイスは、アプリケーション レイヤーからの依存関係の挿入も使われます。</span><span class="sxs-lookup"><span data-stu-id="2b4e0-114">Those interfaces are also used through Dependency Injection from the application layer.</span></span>

![](./media/image13.PNG)

<span data-ttu-id="2b4e0-115">**図 9-12**です。</span><span class="sxs-lookup"><span data-stu-id="2b4e0-115">**Figure 9-12**.</span></span> <span data-ttu-id="2b4e0-116">サンプルは、ドメイン モデル"seedwork"基本クラスとインターフェイスの設定</span><span class="sxs-lookup"><span data-stu-id="2b4e0-116">A sample set of domain model “seedwork" base classes and interfaces</span></span>

<span data-ttu-id="2b4e0-117">これは、多くの開発者は、プロジェクト、正式なフレームワークではない間で共有するコピーと貼り付けを再利用の型です。</span><span class="sxs-lookup"><span data-stu-id="2b4e0-117">This is the type of copy and paste reuse that many developers share between projects, not a formal framework.</span></span> <span data-ttu-id="2b4e0-118">任意のレイヤーまたはライブラリで seedworks ことができます。</span><span class="sxs-lookup"><span data-stu-id="2b4e0-118">You can have seedworks in any layer or library.</span></span> <span data-ttu-id="2b4e0-119">ただし、クラスとインターフェイスのセットは、十分な大きさを取得、可能性がある場合は、1 つのクラス ライブラリを作成します。</span><span class="sxs-lookup"><span data-stu-id="2b4e0-119">However, if the set of classes and interfaces gets big enough, you might want to create a single class library.</span></span>

## <a name="the-custom-entity-base-class"></a><span data-ttu-id="2b4e0-120">カスタム エンティティの基本クラス</span><span class="sxs-lookup"><span data-stu-id="2b4e0-120">The custom Entity base class</span></span>

<span data-ttu-id="2b4e0-121">次のコードは、エンティティの基本クラスの例であり、エンティティ ID など、任意のドメイン エンティティで同じ方法を使用できるコードを配置する[等値演算子](https://msdn.microsoft.com/en-us/library/c35t2ffz.aspx), などです。</span><span class="sxs-lookup"><span data-stu-id="2b4e0-121">The following code is an example of an Entity base class where you can place code that can be used the same way by any domain entity, such as the entity ID, [equality operators](https://msdn.microsoft.com/en-us/library/c35t2ffz.aspx), etc.</span></span>

```csharp
// ENTITY FRAMEWORK CORE 1.1
public abstract class Entity
{
    int? _requestedHashCode;
    int _Id;

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
                _requestedHashCode = this.Id.GetHashCode() \^ 31;
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

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a><span data-ttu-id="2b4e0-122">ドメイン モデル レイヤーにおいてリポジトリ コントラクト (インターフェイス)</span><span class="sxs-lookup"><span data-stu-id="2b4e0-122">Repository contracts (interfaces) in the domain model layer</span></span>

<span data-ttu-id="2b4e0-123">リポジトリのコントラクトは、各集計に使用する、リポジトリのコントラクト要件を表現する .NET インターフェイスだけです。</span><span class="sxs-lookup"><span data-stu-id="2b4e0-123">Repository contracts are simply .NET interfaces that express the contract requirements of the repositories to be used for each aggregate.</span></span> <span data-ttu-id="2b4e0-124">ドメイン モデル内で EF コア コード、またはその他のインフラストラクチャの依存関係、およびコードを使用、自体のリポジトリを実装する必要がありません。リポジトリでは、定義するインターフェイスを実装する必要がありますだけです。</span><span class="sxs-lookup"><span data-stu-id="2b4e0-124">The repositories themselves, with EF Core code or any other infrastructure dependencies and code, must not be implemented within the domain model; the repositories should only implement the interfaces you define.</span></span>

<span data-ttu-id="2b4e0-125">この実習 (ドメイン モデル レイヤーにおいてリポジトリ インターフェイスを配置すること) に関連するパターンは、インターフェイスの区切られたパターンです。</span><span class="sxs-lookup"><span data-stu-id="2b4e0-125">A pattern related to this practice (placing the repository interfaces in the domain model layer) is the Separated Interface pattern.</span></span> <span data-ttu-id="2b4e0-126">として[説明](http://www.martinfowler.com/eaaCatalog/separatedInterface.html)で Martin ファウラー"を 1 つのインターフェイスを定義する区切りインターフェイスを使用してパッケージが、別の実装します。</span><span class="sxs-lookup"><span data-stu-id="2b4e0-126">As [explained](http://www.martinfowler.com/eaaCatalog/separatedInterface.html) by Martin Fowler, “Use Separated Interface to define an interface in one package but implement it in another.</span></span> <span data-ttu-id="2b4e0-127">この方法インターフェイスへの依存関係が必要なクライアントがありますの実装では、完全に注意してください。"</span><span class="sxs-lookup"><span data-stu-id="2b4e0-127">This way a client that needs the dependency to the interface can be completely unaware of the implementation.”</span></span>

<span data-ttu-id="2b4e0-128">ドメイン モデルで定義されている要件への依存関係がインフラストラクチャ/永続化に直接依存されませんが、アプリケーション層 (ここでは、マイクロ サービスの Web API プロジェクト) を有効に区切られたインターフェイス パターンに従うレイヤーです。</span><span class="sxs-lookup"><span data-stu-id="2b4e0-128">Following the Separated Interface pattern enables the application layer (in this case, the Web API project for the microservice) to have a dependency on the requirements defined in the domain model, but not a direct dependency to the infrastructure/persistence layer.</span></span> <span data-ttu-id="2b4e0-129">依存関係の挿入を使用して、インフラストラクチャで実装されると、実装を分離するさらに、永続性レイヤーのリポジトリを使用しています。</span><span class="sxs-lookup"><span data-stu-id="2b4e0-129">In addition, you can use Dependency Injection to isolate the implementation, which is implemented in the infrastructure/ persistence layer using repositories.</span></span>

<span data-ttu-id="2b4e0-130">たとえば、IOrderRepository インターフェイスで次の例では、OrderRepository クラスは、インフラストラクチャ レイヤーで実装する必要があります、どのような操作を定義します。</span><span class="sxs-lookup"><span data-stu-id="2b4e0-130">For example, the following example with the IOrderRepository interface defines what operations the OrderRepository class will need to implement at the infrastructure layer.</span></span> <span data-ttu-id="2b4e0-131">アプリケーションの現在の実装で、コードはクエリは、分割次 CQS アプローチと注文への更新が実装されていないため、データベースに注文を追加するだけが必要です。</span><span class="sxs-lookup"><span data-stu-id="2b4e0-131">In the current implementation of the application, the code just needs to add the order to the database, since queries are split following the CQS approach, and updates to orders are not implemented.</span></span>

```csharp
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);
}

public interface IRepository<T> where T : IAggregateRoot
{
    IUnitOfWork UnitOfWork { get; }
}
```

## <a name="additional-resources"></a><span data-ttu-id="2b4e0-132">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="2b4e0-132">Additional resources</span></span>

-   <span data-ttu-id="2b4e0-133">**Martin Fowler。分離されたインターフェイスです。** 
     [ *http://www.martinfowler.com/eaaCatalog/separatedInterface.html*](http://www.martinfowler.com/eaaCatalog/separatedInterface.html%20)</span><span class="sxs-lookup"><span data-stu-id="2b4e0-133">**Martin Fowler. Separated Interface.**
[*http://www.martinfowler.com/eaaCatalog/separatedInterface.html*](http://www.martinfowler.com/eaaCatalog/separatedInterface.html%20)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="2b4e0-134">[前](net-コア-マイクロ サービスのドメイン-model.md) [次へ] (実装値 objects.md)</span><span class="sxs-lookup"><span data-stu-id="2b4e0-134">[Previous] (net-core-microservice-domain-model.md) [Next] (implement-value-objects.md)</span></span>
