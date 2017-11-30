---
title: "値オブジェクトを実装します。"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |値オブジェクトを実装します。"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: c20bc80d2ddb864a3a0172beb211974426a278a8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-value-objects"></a><span data-ttu-id="59fa0-104">値オブジェクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="59fa0-104">Implementing value objects</span></span>

<span data-ttu-id="59fa0-105">エンティティと集計については、前のセクションで既に説明した、id はエンティティの基本的なです。</span><span class="sxs-lookup"><span data-stu-id="59fa0-105">As discussed in earlier sections about entities and aggregates, identity is fundamental for entities.</span></span> <span data-ttu-id="59fa0-106">ただし、多数のオブジェクトとデータ項目にある、id、および値オブジェクトなど、追跡 id を必要としないシステムです。</span><span class="sxs-lookup"><span data-stu-id="59fa0-106">However, there are many objects and data items in a system that do not require an identity and identity tracking, such as value objects.</span></span>

<span data-ttu-id="59fa0-107">値オブジェクトには、他のエンティティを参照できます。</span><span class="sxs-lookup"><span data-stu-id="59fa0-107">A value object can reference other entities.</span></span> <span data-ttu-id="59fa0-108">など、1 つのポイントから取得する方法について説明するルートを生成するアプリケーションでそのルート オブジェクトの値になります。</span><span class="sxs-lookup"><span data-stu-id="59fa0-108">For example, in an application that generates a route that describes how to get from one point to another, that route would be a value object.</span></span> <span data-ttu-id="59fa0-109">特定のルート上のポイントのスナップショットになりますが、内部的に参照するエンティティと市区町村、道路などもこの提案されたルートは、id はありません。</span><span class="sxs-lookup"><span data-stu-id="59fa0-109">It would be a snapshot of points on a specific route, but this suggested route would not have an identity, even though internally it might refer to entities like City, Road, etc.</span></span>

<span data-ttu-id="59fa0-110">図 9. ~ 13. では、注文集計内のアドレス値オブジェクトを示します。</span><span class="sxs-lookup"><span data-stu-id="59fa0-110">Figure 9-13 shows the Address value object within the Order aggregate.</span></span>

![](./media/image14.png)

<span data-ttu-id="59fa0-111">**図 9. ~ 13.**です。</span><span class="sxs-lookup"><span data-stu-id="59fa0-111">**Figure 9-13**.</span></span> <span data-ttu-id="59fa0-112">順序の集計内のオブジェクトの値に対応します。</span><span class="sxs-lookup"><span data-stu-id="59fa0-112">Address value object within the Order aggregate</span></span>

<span data-ttu-id="59fa0-113">図 9-13 に示すように、複数の属性はエンティティが通常で構成されます。</span><span class="sxs-lookup"><span data-stu-id="59fa0-113">As shown in Figure 9-13, an entity is usually composed of multiple attributes.</span></span> <span data-ttu-id="59fa0-114">たとえば、順序を id を持つエンティティとしてモデル化し、OrderId、OrderDate、OrderItems などの属性のセットの内部で構成されます。しかし、アドレスは、複合型の値だけから成る国、番地、市区町村などのモデル化し、値のオブジェクトとして扱われます必要があります。</span><span class="sxs-lookup"><span data-stu-id="59fa0-114">For example, Order can be modeled as an entity with an identity and composed internally of a set of attributes such as OrderId, OrderDate, OrderItems, etc. But the address, which is simply a complex value composed of country, street, city, etc. must be modeled and treated as a value object.</span></span>

## <a name="important-characteristics-of-value-objects"></a><span data-ttu-id="59fa0-115">値オブジェクトの重要な特性</span><span class="sxs-lookup"><span data-stu-id="59fa0-115">Important characteristics of value objects</span></span>

<span data-ttu-id="59fa0-116">値オブジェクトの 2 つの主な特徴があります。</span><span class="sxs-lookup"><span data-stu-id="59fa0-116">There are two main characteristics for value objects:</span></span>

-   <span data-ttu-id="59fa0-117">Id があるありません。</span><span class="sxs-lookup"><span data-stu-id="59fa0-117">They have no identity.</span></span>

-   <span data-ttu-id="59fa0-118">変更可能なことはできません。</span><span class="sxs-lookup"><span data-stu-id="59fa0-118">They are immutable.</span></span>

<span data-ttu-id="59fa0-119">1 番目の特性は既に説明しました。</span><span class="sxs-lookup"><span data-stu-id="59fa0-119">The first characteristic was already discussed.</span></span> <span data-ttu-id="59fa0-120">不変性は、重要な要件です。</span><span class="sxs-lookup"><span data-stu-id="59fa0-120">Immutability is an important requirement.</span></span> <span data-ttu-id="59fa0-121">値オブジェクトの値、オブジェクトを作成した後に変更可能なことがあります。</span><span class="sxs-lookup"><span data-stu-id="59fa0-121">The values of a value object must be immutable once the object is created.</span></span> <span data-ttu-id="59fa0-122">そのため、オブジェクトを作成するとき、必要な値を指定する必要がありますが、オブジェクトの有効期間中に変更することを許可する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="59fa0-122">Therefore, when the object is constructed, you must provide the required values, but you must not allow them to change during the object’s lifetime.</span></span>

<span data-ttu-id="59fa0-123">値オブジェクトを使用すると、変更できない性質により、パフォーマンスの特定のテクニックを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="59fa0-123">Value objects allow you to perform certain tricks for performance, thanks to their immutable nature.</span></span> <span data-ttu-id="59fa0-124">これは、システムで特に同じ値を持つたくさんある数千の値のオブジェクトのインスタンス、します。</span><span class="sxs-lookup"><span data-stu-id="59fa0-124">This is especially true in systems where there may be thousands of value object instances, many of which have the same values.</span></span> <span data-ttu-id="59fa0-125">変更できない、本来を再利用できること。その値が同じでありの id がないために、交換可能なオブジェクトが存在することができます。</span><span class="sxs-lookup"><span data-stu-id="59fa0-125">Their immutable nature allows them to be reused; they can be interchangeable objects, since their values are the same and they have no identity.</span></span> <span data-ttu-id="59fa0-126">この最適化の種類にできるの違いは、実行速度が遅いソフトウェアとソフトウェア良好なパフォーマンスをことがあります。</span><span class="sxs-lookup"><span data-stu-id="59fa0-126">This type of optimization can sometimes make a difference between software that runs slowly and software with good performance.</span></span> <span data-ttu-id="59fa0-127">もちろん、このような場合は、アプリケーション環境と展開のコンテキストに依存します。</span><span class="sxs-lookup"><span data-stu-id="59fa0-127">Of course, all these cases depend on the application environment and deployment context.</span></span>

## <a name="value-object-implementation-in-c"></a><span data-ttu-id="59fa0-128">C では値オブジェクトの実装\#</span><span class="sxs-lookup"><span data-stu-id="59fa0-128">Value object implementation in C\#</span></span>

<span data-ttu-id="59fa0-129">実装では、観点から (からのオブジェクトの値は、id に基づいている必要がありますいない) すべての属性とその他の基本的な特性の比較に基づいてに等しいかどうかのような基本的なユーティリティ メソッドを持つ値オブジェクトの基本クラスことができます。</span><span class="sxs-lookup"><span data-stu-id="59fa0-129">In terms of implementation, you can have a value object base class that has basic utility methods like equality based on comparison between all the attributes (since a value object must not be based on identity) and other fundamental characteristics.</span></span> <span data-ttu-id="59fa0-130">次の例では、eShopOnContainers から順序マイクロ サービスで使用される、値オブジェクトの基本クラスを示します。</span><span class="sxs-lookup"><span data-stu-id="59fa0-130">The following example shows a value object base class used in the ordering microservice from eShopOnContainers.</span></span>

```csharp
public abstract class ValueObject
{
    protected static bool EqualOperator(ValueObject left, ValueObject right)
    {
        if (ReferenceEquals(left, null) ^ ReferenceEquals(right, null))
        {
            return false;
        }
        return ReferenceEquals(left, null) || left.Equals(right);
    }

    protected static bool NotEqualOperator(ValueObject left, ValueObject right)
    {
        return !(EqualOperator(left, right));
    }

    protected abstract IEnumerable<object> GetAtomicValues();

    public override bool Equals(object obj)
    {
        if (obj == null || obj.GetType() != GetType())
        {
            return false;
        }

        ValueObject other = (ValueObject)obj;
        IEnumerator<object> thisValues = GetAtomicValues().GetEnumerator();
        IEnumerator<object> otherValues = other.GetAtomicValues().GetEnumerator();
        while (thisValues.MoveNext() && otherValues.MoveNext())
        {
            if (ReferenceEquals(thisValues.Current, null) ^
                ReferenceEquals(otherValues.Current, null))
            {
                return false;
            }

            if (thisValues.Current != null &&
                !thisValues.Current.Equals(otherValues.Current))
            {
                return false;
            }
        }
        return !thisValues.MoveNext() && !otherValues.MoveNext();
    }
    // Other utilility methods
}
```

<span data-ttu-id="59fa0-131">次の例に示すように、アドレス値オブジェクトと同様、実際の値オブジェクトを実装するときにこのクラスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="59fa0-131">You can use this class when implementing your actual value object, as with the Address value object shown in the following example:</span></span>

```csharp
public class Address : ValueObject
{
    public String Street { get; private set; }
    public String City { get; private set; }
    public String State { get; private set; }
    public String Country { get; private set; }
    public String ZipCode { get; private set; }

    public Address(string street, string city, string state,
        string country, string zipcode)
    {
        Street = street;
        City = city;
        State = state;
        Country = country;
        ZipCode = zipcode;
    }

    protected override IEnumerable<object> GetAtomicValues()
    {
        yield return Street;
        yield return City;
        yield return State;
        yield return Country;
        yield return ZipCode;
    }
}
```

## <a name="hiding-the-identity-characteristic-when-using-ef-core-to-persist-value-objects"></a><span data-ttu-id="59fa0-132">EF コアを使用して値オブジェクトを保持する場合、識別特性を非表示にします。</span><span class="sxs-lookup"><span data-stu-id="59fa0-132">Hiding the identity characteristic when using EF Core to persist value objects</span></span>

<span data-ttu-id="59fa0-133">現在のバージョン (EF コア 1.1) では使用できないことを EF コアを使用する場合、制限[複合型](https://docs.microsoft.com/de-de/dotnet/api/system.componentmodel.dataannotations.schema.complextypeattribute?view=netframework-4.7)EF で定義されている 6.x です。</span><span class="sxs-lookup"><span data-stu-id="59fa0-133">A limitation when using EF Core is that in its current version (EF Core 1.1) you cannot use [complex types](https://docs.microsoft.com/de-de/dotnet/api/system.componentmodel.dataannotations.schema.complextypeattribute?view=netframework-4.7) as defined in EF 6.x.</span></span> <span data-ttu-id="59fa0-134">そのため、EF エンティティとして、オブジェクトの値を格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="59fa0-134">Therefore, you must store your value object as an EF entity.</span></span> <span data-ttu-id="59fa0-135">ただし、クリア、id がオブジェクトの値が含まれるモデルで重要でないことを行うようには、その ID を非表示にできます。</span><span class="sxs-lookup"><span data-stu-id="59fa0-135">However, you can hide its ID so you make clear that the identity is not important in the model that the value object is part of.</span></span> <span data-ttu-id="59fa0-136">ID を非表示にする、シャドウ プロパティとして、ID を使用することです。</span><span class="sxs-lookup"><span data-stu-id="59fa0-136">You hide the ID is by using the ID as a shadow property.</span></span> <span data-ttu-id="59fa0-137">その構成モデルの ID を非表示に設定されているためインフラストラクチャ レベルで、ドメイン モデルに対して透過的になり、インフラストラクチャ実装は、今後変更可能性があります。</span><span class="sxs-lookup"><span data-stu-id="59fa0-137">Since that configuration for hiding the ID in the model is set up in the infrastructure level, it will be transparent for your domain model, and its infrastructure implementation could change in the future.</span></span>

<span data-ttu-id="59fa0-138">EShopOnContainers での EF のコア インフラストラクチャで必要な非表示の ID インフラストラクチャ プロジェクトで Fluent API を使用して DbContext レベルでは、次のように実装されます。</span><span class="sxs-lookup"><span data-stu-id="59fa0-138">In eShopOnContainers, the hidden ID needed by EF Core infrastructure is implemented in the following way in the DbContext level, using Fluent API at the infrastructure project.</span></span>

```csharp
// Fluent API within the OrderingContext:DbContext in the
// Ordering.Infrastructure project

void ConfigureAddress(EntityTypeBuilder<Address> addressConfiguration)
{
    addressConfiguration.ToTable("address", DEFAULT_SCHEMA);
    addressConfiguration.Property<int>("Id").IsRequired();
    addressConfiguration.HasKey("Id");
}
```

<span data-ttu-id="59fa0-139">そのため、ID が、ドメイン モデルの観点から、非表示、今後は、値オブジェクトのインフラストラクチャでしたも実装する複合型または別の方法として。</span><span class="sxs-lookup"><span data-stu-id="59fa0-139">Therefore, the ID is hidden from the domain model point of view, and in the future, the value object infrastructure could also be implemented as a complex type or another way.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="59fa0-140">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="59fa0-140">Additional resources</span></span>

-   <span data-ttu-id="59fa0-141">**Martin Fowler。ValueObject パターン**
    [*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)</span><span class="sxs-lookup"><span data-stu-id="59fa0-141">**Martin Fowler. ValueObject pattern**
[*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)</span></span>

-   <span data-ttu-id="59fa0-142">**Eric Evans。ドメインに基づく設計: は Tackling Complexity in the Heart of Software です。**</span><span class="sxs-lookup"><span data-stu-id="59fa0-142">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software.**</span></span> <span data-ttu-id="59fa0-143">(予約値オブジェクトの説明を含む)。[ *https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span><span class="sxs-lookup"><span data-stu-id="59fa0-143">(Book; includes a discussion of value objects) [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span></span>

-   <span data-ttu-id="59fa0-144">**Vaughn Vernon。ドメインに基づく設計の実装です。**</span><span class="sxs-lookup"><span data-stu-id="59fa0-144">**Vaughn Vernon. Implementing Domain-Driven Design.**</span></span> <span data-ttu-id="59fa0-145">(予約値オブジェクトの説明を含む)。[ *https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span><span class="sxs-lookup"><span data-stu-id="59fa0-145">(Book; includes a discussion of value objects) [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span></span>

-   <span data-ttu-id="59fa0-146">**プロパティをシャドウ**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span><span class="sxs-lookup"><span data-stu-id="59fa0-146">**Shadow Properties**
[*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span></span>

-   <span data-ttu-id="59fa0-147">**複合型および値オブジェクト**です。</span><span class="sxs-lookup"><span data-stu-id="59fa0-147">**Complex types and/or value objects**.</span></span> <span data-ttu-id="59fa0-148">EF コア GitHub リポジトリ ([問題] タブ) でディスカッション[ *https://github.com/aspnet/EntityFramework/issues/246*](https://github.com/aspnet/EntityFramework/issues/246)</span><span class="sxs-lookup"><span data-stu-id="59fa0-148">Discussion in the EF Core GitHub repo (Issues tab) [*https://github.com/aspnet/EntityFramework/issues/246*](https://github.com/aspnet/EntityFramework/issues/246)</span></span>

-   <span data-ttu-id="59fa0-149">**ValueObject.cs です。**</span><span class="sxs-lookup"><span data-stu-id="59fa0-149">**ValueObject.cs.**</span></span> <span data-ttu-id="59fa0-150">オブジェクト クラスを基本値 eShopOnContainers にします。</span><span class="sxs-lookup"><span data-stu-id="59fa0-150">Base value object class in eShopOnContainers.</span></span>
    [<span data-ttu-id="59fa0-151">*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs*</span><span class="sxs-lookup"><span data-stu-id="59fa0-151">*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs*</span></span>](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs)

-   <span data-ttu-id="59fa0-152">**クラスに対応します。**</span><span class="sxs-lookup"><span data-stu-id="59fa0-152">**Address class.**</span></span> <span data-ttu-id="59fa0-153">サンプル値のオブジェクト クラス eShopOnContainers です。</span><span class="sxs-lookup"><span data-stu-id="59fa0-153">Sample value object class in eShopOnContainers.</span></span>
    [<span data-ttu-id="59fa0-154">*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs*</span><span class="sxs-lookup"><span data-stu-id="59fa0-154">*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs*</span></span>](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs)


>[!div class="step-by-step"]
<span data-ttu-id="59fa0-155">[前](seedwork-domain-model-base-classes-interfaces.md) [次へ] (列挙型のクラスの over-enum-types.md)</span><span class="sxs-lookup"><span data-stu-id="59fa0-155">[Previous] (seedwork-domain-model-base-classes-interfaces.md) [Next] (enumeration-classes-over-enum-types.md)</span></span>
