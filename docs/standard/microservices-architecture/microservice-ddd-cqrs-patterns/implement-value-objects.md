---
title: "値オブジェクトの実装"
description: ".NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | 値オブジェクトの実装"
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
ms.openlocfilehash: ce81991e48fb5eb4eb3bed3dd2fcfe1734ca7bac
ms.sourcegitcommit: 1c0b0f082b3f300e54b4d069b317ac724c88ddc3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/16/2018
---
# <a name="implementing-value-objects"></a><span data-ttu-id="c8832-104">値オブジェクトの実装</span><span class="sxs-lookup"><span data-stu-id="c8832-104">Implementing value objects</span></span>

<span data-ttu-id="c8832-105">これまでのエンティティと集計に関するセクションで説明したように、ID はエンティティの基礎です。</span><span class="sxs-lookup"><span data-stu-id="c8832-105">As discussed in earlier sections about entities and aggregates, identity is fundamental for entities.</span></span> <span data-ttu-id="c8832-106">一方、システムには、ID と ID の追跡を必要としないオブジェクトとデータ項目が多数あります。たとえば、値オブジェクトなどです。</span><span class="sxs-lookup"><span data-stu-id="c8832-106">However, there are many objects and data items in a system that do not require an identity and identity tracking, such as value objects.</span></span>

<span data-ttu-id="c8832-107">値オブジェクトは他のエンティティを参照できます。</span><span class="sxs-lookup"><span data-stu-id="c8832-107">A value object can reference other entities.</span></span> <span data-ttu-id="c8832-108">たとえば、あるポイントから別のポイントに到達する方法を示すルートを生成するアプリケーションの場合、そのルートが値オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="c8832-108">For example, in an application that generates a route that describes how to get from one point to another, that route would be a value object.</span></span> <span data-ttu-id="c8832-109">これは特定のルート上にあるポイントのスナップショットですが、内部的には City、Road などのエンティティを参照していても、この提案されるルートに ID はありません。</span><span class="sxs-lookup"><span data-stu-id="c8832-109">It would be a snapshot of points on a specific route, but this suggested route would not have an identity, even though internally it might refer to entities like City, Road, etc.</span></span>

<span data-ttu-id="c8832-110">図 9-13 は、Order 集計内の Address 値オブジェクトを示しています。</span><span class="sxs-lookup"><span data-stu-id="c8832-110">Figure 9-13 shows the Address value object within the Order aggregate.</span></span>

![](./media/image14.png)

<span data-ttu-id="c8832-111">**図 9-13**.</span><span class="sxs-lookup"><span data-stu-id="c8832-111">**Figure 9-13**.</span></span> <span data-ttu-id="c8832-112">Order 集計内の Address 値オブジェクト</span><span class="sxs-lookup"><span data-stu-id="c8832-112">Address value object within the Order aggregate</span></span>

<span data-ttu-id="c8832-113">図 9-13 に示すように、通常、エンティティは複数の属性で構成されます。</span><span class="sxs-lookup"><span data-stu-id="c8832-113">As shown in Figure 9-13, an entity is usually composed of multiple attributes.</span></span> <span data-ttu-id="c8832-114">たとえば、`Order` エンティティは、ID があるエンティティとしてモデル化し、内部的に OrderId、OrderDate、OrderItems などの一連の属性で構成することができます。ただし、住所は、単に国、市区町村、番地などで構成された複合値であり、このドメイン内に ID はないため、値をモデル化し、値オブジェクトとして扱う必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8832-114">For example, the `Order` entity can be modeled as an entity with an identity and composed internally of a set of attributes such as OrderId, OrderDate, OrderItems, etc. But the address, which is simply a complex value composed of country, street, city, etc. and has no identity in this domain,  must be modeled and treated as a value object.</span></span>

## <a name="important-characteristics-of-value-objects"></a><span data-ttu-id="c8832-115">値オブジェクトの重要な特性</span><span class="sxs-lookup"><span data-stu-id="c8832-115">Important characteristics of value objects</span></span>

<span data-ttu-id="c8832-116">値オブジェクトには主に 2 つの特性があります。</span><span class="sxs-lookup"><span data-stu-id="c8832-116">There are two main characteristics for value objects:</span></span>

-   <span data-ttu-id="c8832-117">ID がない。</span><span class="sxs-lookup"><span data-stu-id="c8832-117">They have no identity.</span></span>

-   <span data-ttu-id="c8832-118">不変である。</span><span class="sxs-lookup"><span data-stu-id="c8832-118">They are immutable.</span></span>

<span data-ttu-id="c8832-119">1 つ目の特性については既に説明しました。</span><span class="sxs-lookup"><span data-stu-id="c8832-119">The first characteristic was already discussed.</span></span> <span data-ttu-id="c8832-120">不変性は重要な要件です。</span><span class="sxs-lookup"><span data-stu-id="c8832-120">Immutability is an important requirement.</span></span> <span data-ttu-id="c8832-121">値オブジェクトが作成された後は、その値を不変にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8832-121">The values of a value object must be immutable once the object is created.</span></span> <span data-ttu-id="c8832-122">そのため、オブジェクトの構築時に必要な値を指定する必要がありますが、オブジェクトの有効期間中は変更を許可しない必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8832-122">Therefore, when the object is constructed, you must provide the required values, but you must not allow them to change during the object’s lifetime.</span></span>

<span data-ttu-id="c8832-123">値オブジェクトを使用すると、不変の性質がパフォーマンスのために役立つことがあります。</span><span class="sxs-lookup"><span data-stu-id="c8832-123">Value objects allow you to perform certain tricks for performance, thanks to their immutable nature.</span></span> <span data-ttu-id="c8832-124">特に、何千もの値オブジェクト インスタンスが存在する可能性があり、インスタンスの多くが同じ値を持つシステムで役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="c8832-124">This is especially true in systems where there may be thousands of value object instances, many of which have the same values.</span></span> <span data-ttu-id="c8832-125">不変の性質なので、再利用することができます。値が同じで、ID を持たないので、相互に交換可能なオブジェクトにすることができます。</span><span class="sxs-lookup"><span data-stu-id="c8832-125">Their immutable nature allows them to be reused; they can be interchangeable objects, since their values are the same and they have no identity.</span></span> <span data-ttu-id="c8832-126">このような最適化で、低速で実行されるソフトウェアとパフォーマンスが良好なソフトウェアの間で違いが生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="c8832-126">This type of optimization can sometimes make a difference between software that runs slowly and software with good performance.</span></span> <span data-ttu-id="c8832-127">当然ながら、このようないずれの場合でも、アプリケーション環境と展開コンテキストによって変わります。</span><span class="sxs-lookup"><span data-stu-id="c8832-127">Of course, all these cases depend on the application environment and deployment context.</span></span>

## <a name="value-object-implementation-in-c"></a><span data-ttu-id="c8832-128">C\# での値オブジェクトの実装</span><span class="sxs-lookup"><span data-stu-id="c8832-128">Value object implementation in C\#</span></span>

<span data-ttu-id="c8832-129">実装の観点からは、(値オブジェクトは ID に基づいてはならないので) すべての属性と他の基本的な特性の比較に基づいて、等値などの基本的なユーティリティ メソッドを持つ値オブジェクトの基底クラスを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="c8832-129">In terms of implementation, you can have a value object base class that has basic utility methods like equality based on comparison between all the attributes (since a value object must not be based on identity) and other fundamental characteristics.</span></span> <span data-ttu-id="c8832-130">次の例は、eShopOnContainers の注文マイクロサービスで使用される値オブジェクトの基底クラスを示しています。</span><span class="sxs-lookup"><span data-stu-id="c8832-130">The following example shows a value object base class used in the ordering microservice from eShopOnContainers.</span></span>

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

    public override int GetHashCode()
    {
        return GetAtomicValues()
         .Select(x => x != null ? x.GetHashCode() : 0)
         .Aggregate((x, y) => x ^ y);
    }        
    // Other utilility methods
}
```

<span data-ttu-id="c8832-131">次の例に示す Address 値オブジェクトと同様に、実際の値オブジェクトを実装するときにこのクラスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="c8832-131">You can use this class when implementing your actual value object, as with the Address value object shown in the following example:</span></span>

```csharp
public class Address : ValueObject
{
    public String Street { get; private set; }
    public String City { get; private set; }
    public String State { get; private set; }
    public String Country { get; private set; }
    public String ZipCode { get; private set; }

    private Address() { }

    public Address(string street, string city, string state, string country, string zipcode)
    {
        Street = street;
        City = city;
        State = state;
        Country = country;
        ZipCode = zipcode;
    }

    protected override IEnumerable<object> GetAtomicValues()
    {
        // Using a yield return statement to return each element one at a time
        yield return Street;
        yield return City;
        yield return State;
        yield return Country;
        yield return ZipCode;
    }
}
```

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20"></a><span data-ttu-id="c8832-132">EF Core 2.0 でデータベース内の値オブジェクトを永続化する方法</span><span class="sxs-lookup"><span data-stu-id="c8832-132">How to persist value objects in the database with EF Core 2.0</span></span>

<span data-ttu-id="c8832-133">ここまでは、ドメイン モデルで値オブジェクトを定義する方法について説明しました。</span><span class="sxs-lookup"><span data-stu-id="c8832-133">You just saw how to define a value object in your domain model.</span></span> <span data-ttu-id="c8832-134">それでは、通常は ID のあるエンティティをターゲットとする Entity Framework (EF) Core を使用して、データベースに永続化するにはどうすればよいでしょうか。</span><span class="sxs-lookup"><span data-stu-id="c8832-134">But, how can you actually persist it into the database through Entity Framework (EF) Core which usually targets entities with identity?</span></span>

### <a name="background-and-older-approaches-using-ef-core-11"></a><span data-ttu-id="c8832-135">EF Core 1.1 を使用する背景と以前のアプローチ</span><span class="sxs-lookup"><span data-stu-id="c8832-135">Background and older approaches using EF Core 1.1</span></span>

<span data-ttu-id="c8832-136">背景として、EF Core 1.0 と 1.1 を使用する場合、従来の .NET Framework で EF 6.x で定義されているような[複合型](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute)を使用できないという制限がありました。</span><span class="sxs-lookup"><span data-stu-id="c8832-136">As background, a limitation when using EF Core 1.0 and 1.1 was that you cannot use  [complex types](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) as defined in EF 6.x in the traditional .NET Framework.</span></span> <span data-ttu-id="c8832-137">そのため、EF Core 1.0 または 1.1 を使用する場合、値オブジェクトを ID フィールドを持つ EF エンティティとして格納する必要がありました。</span><span class="sxs-lookup"><span data-stu-id="c8832-137">Therefore, if using EF Core 1.0 or 1.1, you needed to store your value object as an EF entity with an ID field.</span></span> <span data-ttu-id="c8832-138">そこで、ID を持たない値オブジェクトのように見えるように、ID を非表示にすることがありました。これで、値オブジェクトの ID がドメイン モデルで重要ではないことがはっきりします。</span><span class="sxs-lookup"><span data-stu-id="c8832-138">Then, so it looked more like a value object with no identity, you could hide its ID so you make clear that the identity of a value object is not important in the domain model.</span></span> <span data-ttu-id="c8832-139">この ID を非表示にするには、[シャドウ プロパティ](https://docs.microsoft.com/ef/core/modeling/shadow-properties )として ID を使用します。</span><span class="sxs-lookup"><span data-stu-id="c8832-139">You could hide that ID by using the ID as a [shadow property](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span></span> <span data-ttu-id="c8832-140">モデル内の ID を非表示にする構成は EF インフラストラクチャ レベルで設定されるため、ドメイン モデルでも透過的になります。</span><span class="sxs-lookup"><span data-stu-id="c8832-140">Since that configuration for hiding the ID in the model is set up in the EF infrastructure level, it would be kind of transparent for your domain model.</span></span>

<span data-ttu-id="c8832-141">eShopOnContainers の初期バージョン (.NET Core 1.1) では、EF Core インフラストラクチャに必要な非表示の ID は、次のように、インフラストラクチャ プロジェクトで Fluent API を使用して DbContext レベルで実装されていました。</span><span class="sxs-lookup"><span data-stu-id="c8832-141">In the initial version of eShopOnContainers (.NET Core 1.1), the hidden ID needed by EF Core infrastructure was implemented in the following way in the DbContext level, using Fluent API at the infrastructure project.</span></span> <span data-ttu-id="c8832-142">そのため、ID はドメイン モデルの観点からは非表示でしたが、インフラストラクチャには存在していました。</span><span class="sxs-lookup"><span data-stu-id="c8832-142">Therefore, the ID was hidden from the domain model point of view, but still present in the infrastructure.</span></span>

```csharp
// Old approach with EF Core 1.1
// Fluent API within the OrderingContext:DbContext in the Infrastructure project
void ConfigureAddress(EntityTypeBuilder<Address> addressConfiguration) 
{
    addressConfiguration.ToTable("address", DEFAULT_SCHEMA); 

    addressConfiguration.Property<int>("Id")  // Id is a shadow property
        .IsRequired();
    addressConfiguration.HasKey("Id");   // Id is a shadow property
}
```

<span data-ttu-id="c8832-143">ただし、その値オブジェクトのデータベースへの永続化は、別のテーブルの通常のエンティティと同様に実行されていました。</span><span class="sxs-lookup"><span data-stu-id="c8832-143">However, the persistence of that value object into the database was performed like a regular entity in a different table.</span></span>

<span data-ttu-id="c8832-144">EF Core 2.0 には、値オブジェクトを永続化するための新しく優れた方法があります。</span><span class="sxs-lookup"><span data-stu-id="c8832-144">With EF Core 2.0, there are new and better ways to persist value objects.</span></span>

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20"></a><span data-ttu-id="c8832-145">EF Core 2.0 で所有エンティティ型として値オブジェクトを永続化する</span><span class="sxs-lookup"><span data-stu-id="c8832-145">Persist value objects as owned entity types in EF Core 2.0</span></span>

<span data-ttu-id="c8832-146">DDD の標準の値オブジェクト パターンと EF Core の所有エンティティ型の間にいくつかのギャップがあるとしても、現在は EF Core 2.0 を使用して値オブジェクトを永続化する方法が最善です。</span><span class="sxs-lookup"><span data-stu-id="c8832-146">Even with some gaps between the canonical value object pattern in DDD and the owned entity type in EF Core, it's currently the best way to persist value objects with EF Core 2.0.</span></span> <span data-ttu-id="c8832-147">制限事項については、このセクションの末尾を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8832-147">You can see limitations at the end of this section.</span></span>

<span data-ttu-id="c8832-148">所有エンティティ型の機能は、EF Core バージョン 2.0 以降に追加されました。</span><span class="sxs-lookup"><span data-stu-id="c8832-148">The owned entity type feature was added to EF Core since version 2.0.</span></span>

<span data-ttu-id="c8832-149">所有エンティティ型を使用すると、ドメイン モデルで明示的に定義された独自の ID を持たない型をマップし、任意のエンティティ内で値オブジェクトなどのプロパティとして使用することができます。</span><span class="sxs-lookup"><span data-stu-id="c8832-149">An owned entity type allows you to map types that do not have their own identity explicitely defined in the domain model and are used as properties, such as a value object, within any of your entities.</span></span> <span data-ttu-id="c8832-150">所有エンティティ型は、同じ CLR 型を別のエンティティ型と共有します。</span><span class="sxs-lookup"><span data-stu-id="c8832-150">An owned entity type shares the same CLR type with another entity type.</span></span> <span data-ttu-id="c8832-151">定義となるナビゲーションを含むエンティティは、所有者エンティティです。</span><span class="sxs-lookup"><span data-stu-id="c8832-151">The entity containing the defining navigation is the owner entity.</span></span> <span data-ttu-id="c8832-152">所有者のクエリを実行すると、所有型が既定で含まれます。</span><span class="sxs-lookup"><span data-stu-id="c8832-152">When querying the owner, the owned types are included by default.</span></span>

<span data-ttu-id="c8832-153">ドメイン モデルのみを見ると、所有型には ID がないように見えます。</span><span class="sxs-lookup"><span data-stu-id="c8832-153">Just by looking at the domain model, an owned type looks like it doesn’t have any identity.</span></span>
<span data-ttu-id="c8832-154">実際には所有型に ID はありますが、所有者ナビゲーション プロパティはこの ID の一部です。</span><span class="sxs-lookup"><span data-stu-id="c8832-154">However, under the covers, owned types do have identity, but the owner navigation property is part of this identity.</span></span>

<span data-ttu-id="c8832-155">所有型のインスタンスの ID は、完全に独自のものではありません。</span><span class="sxs-lookup"><span data-stu-id="c8832-155">The identity of instances of own types is not completely their own.</span></span> <span data-ttu-id="c8832-156">この ID は 3 つのコンポーネントで構成されています。</span><span class="sxs-lookup"><span data-stu-id="c8832-156">It consists of three components:</span></span>

- <span data-ttu-id="c8832-157">所有者の ID</span><span class="sxs-lookup"><span data-stu-id="c8832-157">The identity of the owner</span></span>

- <span data-ttu-id="c8832-158">これらを指すナビゲーション プロパティ</span><span class="sxs-lookup"><span data-stu-id="c8832-158">The navigation property pointing to them</span></span>

- <span data-ttu-id="c8832-159">所有型のコレクションの場合は、独立したコンポーネント (EF Core 2.0 ではまだサポートされていません)。</span><span class="sxs-lookup"><span data-stu-id="c8832-159">In the case of collections of owned types, an independent component (not yet supported in EF Core 2.0).</span></span>

<span data-ttu-id="c8832-160">たとえば、eShopOnContainers の Ordering ドメイン モデルでは、Order エンティティの一部である Address 値オブジェクトは、所有者エンティティ (Order エンティティ) 内の所有エンティティ型として実装されます。</span><span class="sxs-lookup"><span data-stu-id="c8832-160">For example, in the Ordering domain model at eShopOnContainers, as part of the Order entity, the Address value object is implemented as an owned entity type within the owner entity, which is the Order entity.</span></span> <span data-ttu-id="c8832-161">Address は、ドメイン モデルに定義されている ID プロパティのない型です。</span><span class="sxs-lookup"><span data-stu-id="c8832-161">Address is a type with no identity property defined in the domain model.</span></span> <span data-ttu-id="c8832-162">特定の注文の配送先住所を指定するために、Order 型のプロパティとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="c8832-162">It is used as a property of the Order type to specify the shipping address for a particular order.</span></span>

<span data-ttu-id="c8832-163">規約によって、所有されている型に対してシャドウ主キーが作成され、テーブル分割を利用し、同じテーブルに所有者としてマップされます。</span><span class="sxs-lookup"><span data-stu-id="c8832-163">By convention, a shadow primary key is created for the owned type and it will be mapped to the same table as the owner by using table splitting.</span></span> <span data-ttu-id="c8832-164">そのため、従来の .NET Framework の EF6 で複合型を使用する方法と同様に所有型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c8832-164">This allows to use owned types similarly to how complex types are used in EF6 in the traditional .NET Framework.</span></span>

<span data-ttu-id="c8832-165">EF Core の規約で所有型が検出されることはないので、明示的に宣言する必要がある点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="c8832-165">It is important to note that owned types are never discovered by convention in EF Core, so you have to declare them explicitly.</span></span>

<span data-ttu-id="c8832-166">eShopOnContainers では、OnModelCreating() メソッド内の OrderingContext.cs に複数のインフラストラクチャ構成が適用されています。</span><span class="sxs-lookup"><span data-stu-id="c8832-166">In eShopOnContainers, at the OrderingContext.cs, within the OnModelCreating() method, there are multiple infrastructure configuration being applied.</span></span> <span data-ttu-id="c8832-167">そのうちの 1 つが Order エンティティに関連しています。</span><span class="sxs-lookup"><span data-stu-id="c8832-167">One of them is related to the Order entity.</span></span>

```csharp
// Part of the OrderingContext.cs class at the Ordering.Infrastructure project
// 
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
    modelBuilder.ApplyConfiguration(new ClientRequestEntityTypeConfiguration());
    modelBuilder.ApplyConfiguration(new PaymentMethodEntityTypeConfiguration());
    modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
    modelBuilder.ApplyConfiguration(new OrderItemEntityTypeConfiguration());
    //...Additional type configurations
}
```

<span data-ttu-id="c8832-168">次のコードでは、Order エンティティについて永続化インフラストラクチャが定義されています。</span><span class="sxs-lookup"><span data-stu-id="c8832-168">In the following code, the persistence infrastructure is defined for the Order entity:</span></span>

```csharp
// Part of the OrderEntityTypeConfiguration.cs class 
// 
public void Configure(EntityTypeBuilder<Order> orderConfiguration)
{
    orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);
    orderConfiguration.HasKey(o => o.Id);
    orderConfiguration.Ignore(b => b.DomainEvents);
    orderConfiguration.Property(o => o.Id)
        .ForSqlServerUseSequenceHiLo("orderseq", OrderingContext.DEFAULT_SCHEMA);

    //Address value object persisted as owned entity in EF Core 2.0
    orderConfiguration.OwnsOne(o => o.Address);

    orderConfiguration.Property<DateTime>("OrderDate").IsRequired();
    
    //...Additional validations, constraints and code...
    //...
}
```

<span data-ttu-id="c8832-169">前のコードでは、`orderConfiguration.OwnsOne(o => o.Address)` メソッドは、`Address` プロパティが `Order` 型の所有エンティティであることを指定しています。</span><span class="sxs-lookup"><span data-stu-id="c8832-169">In the previous code, the `orderConfiguration.OwnsOne(o => o.Address)` method specifies that the `Address` property is an owned entity of the `Order` type.</span></span>

<span data-ttu-id="c8832-170">既定の EF Core 規約では、所有エンティティ型のプロパティのデータベース列に `EntityProperty_OwnedEntityProperty` と名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="c8832-170">By default, EF Core conventions name the database columns for the properties of the owned entity type as `EntityProperty_OwnedEntityProperty`.</span></span> <span data-ttu-id="c8832-171">そのため、`Address` の内部プロパティは、`Orders` テーブルで `Address_Street`、`Address_City` (`State`、`Country`、`ZipCode` など) という名前で表示されます。</span><span class="sxs-lookup"><span data-stu-id="c8832-171">Therefore, the internal properties of `Address` will appear in the `Orders` table with the names `Address_Street`, `Address_City` (and so on for `State`, `Country` and `ZipCode`).</span></span>

<span data-ttu-id="c8832-172">`Property().HasColumnName()` fluent メソッドを付加して、これらの列の名前を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="c8832-172">You can append the `Property().HasColumnName()` fluent method to rename those columns.</span></span> <span data-ttu-id="c8832-173">`Address` がパブリック プロパティの場合、マッピングは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="c8832-173">In the case where `Address` is a public property, the mappings would be like the following:</span></span>

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

<span data-ttu-id="c8832-174">fluent マッピングでは、`OwnsOne` メソッドを連鎖させることができます。</span><span class="sxs-lookup"><span data-stu-id="c8832-174">It is possible to chain the `OwnsOne` method in a fluent mapping.</span></span> <span data-ttu-id="c8832-175">次の仮定例では、`OrderDetails` が `BillingAddress` と `ShippingAddress` を所有しています (いずれも `Address` 型です)。</span><span class="sxs-lookup"><span data-stu-id="c8832-175">In the following hypothetical example, `OrderDetails` owns `BillingAddress` and `ShippingAddress`, which are both `Address` types.</span></span> <span data-ttu-id="c8832-176">また、`OrderDetails` は `Order` 型に所有されています。</span><span class="sxs-lookup"><span data-stu-id="c8832-176">Then `OrderDetails` is owned by the `Order` type.</span></span>

```csharp
orderConfiguration.OwnsOne(p => p.OrderDetails, cb =>
    {
        cb.OwnsOne(c => c.BillingAddress);
        cb.OwnsOne(c => c.ShippingAddress);
    });
//...
//...
public class Order
{
    public int Id { get; set; }
    public OrderDetails OrderDetails { get; set; }
}

public class OrderDetails
{
    public Address BillingAddress { get; set; }
    public Address ShippingAddress { get; set; }
}

public class Address
{
    public string Street { get; set; }
    public string City { get; set; }
}
```

### <a name="additional-details-on-owned-entity-types"></a><span data-ttu-id="c8832-177">所有エンティティ型に関するその他の詳細情報</span><span class="sxs-lookup"><span data-stu-id="c8832-177">Additional details on owned entity types</span></span>

<span data-ttu-id="c8832-178">•   所有型は、OwnsOne fluent API を使用してナビゲーション プロパティを特定の型に構成するときに定義されます。</span><span class="sxs-lookup"><span data-stu-id="c8832-178">•   Owned types are defined when you configure a navigation property to a particular type using the OwnsOne fluent API.</span></span>

<span data-ttu-id="c8832-179">•   メタデータ モデルの所有型の定義は、所有者型、ナビゲーション プロパティ、所有型の CLR 型のコンポジットです。</span><span class="sxs-lookup"><span data-stu-id="c8832-179">•   The definition of an owned type in our metadata model is a composite of: the owner type, the navigation property, and the CLR type of the owned type.</span></span>

<span data-ttu-id="c8832-180">•   スタック内の所有型インスタンスの ID (キー) は、所有者型の ID と所有型の定義のコンポジットです。</span><span class="sxs-lookup"><span data-stu-id="c8832-180">•   The identity (key) of an owned type instance in our stack is a composite of the identity of the owner type and the definition of the owned type.</span></span>

#### <a name="owned-entities-capabilities"></a><span data-ttu-id="c8832-181">所有エンティティの機能:</span><span class="sxs-lookup"><span data-stu-id="c8832-181">Owned entities capabilities:</span></span>

<span data-ttu-id="c8832-182">•   所有型は、他の所有 (入れ子にされた所有型) エンティティまたは非所有 (他のエンティティに対する通常の参照ナビゲーション プロパティ) エンティティを参照できます。</span><span class="sxs-lookup"><span data-stu-id="c8832-182">•   Owned type can reference other entities, either owned (nested owned types) or non-owned (regular reference navigation properties to other entities).</span></span>

<span data-ttu-id="c8832-183">•   同じ所有者エンティティの同じ CLR 型を、個別のナビゲーション プロパティを使用して異なる所有型としてマップすることができます。</span><span class="sxs-lookup"><span data-stu-id="c8832-183">•   You can map the same CLR type as different owned types in the same owner entity through separate navigation properties.</span></span>

<span data-ttu-id="c8832-184">•   テーブル分割は規約で設定されますが、ToTable を使用して所有型を別のテーブルにマップすることでオプト アウトすることができます。</span><span class="sxs-lookup"><span data-stu-id="c8832-184">•   Table splitting is setup by convention, but you can opt out by mapping the owned type to a different table using ToTable.</span></span>

<span data-ttu-id="c8832-185">•   Eager の読み込みは、所有型に対して自動的に実行されます。つまり、クエリで Include () を呼び出す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c8832-185">•   Eager loading is performed automatically on owned types, i.e. no need to call Include() on the query.</span></span>

#### <a name="owned-entities-limitations"></a><span data-ttu-id="c8832-186">所有エンティティの制限事項:</span><span class="sxs-lookup"><span data-stu-id="c8832-186">Owned entities limitations:</span></span>

<span data-ttu-id="c8832-187">•   所有型の DbSet<T> を作成することはできません (仕様)。</span><span class="sxs-lookup"><span data-stu-id="c8832-187">•   You cannot create a DbSet<T> of an owned type (by design).</span></span>

<span data-ttu-id="c8832-188">•   所有型に対して ModelBuilder.Entity<T>() を呼び出すことはできません (現時点では仕様)。</span><span class="sxs-lookup"><span data-stu-id="c8832-188">•   You cannot call ModelBuilder.Entity<T>() on owned types (currently by design).</span></span>

<span data-ttu-id="c8832-189">•   所有型のコレクションはまだありません (ただし、EF Core 2.0 の後のバージョンではサポートされる予定です)。</span><span class="sxs-lookup"><span data-stu-id="c8832-189">•   No collections of owned types yet (but they will be supported in versions after EF Core 2.0).</span></span>

<span data-ttu-id="c8832-190">•   属性を介した構成はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="c8832-190">•   No support for configuring them via an attribute.</span></span>

<span data-ttu-id="c8832-191">•   同じテーブル内の所有者とマップされている (つまり、テーブル分割を使用している) 省略可能な (つまり、null を許容する) 所有型はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="c8832-191">•   No support for optional (i.e. nullable) owned types that are mapped with the owner in the same table (i.e. using table splitting).</span></span> <span data-ttu-id="c8832-192">これは、null の場合に個別の監視機能を持たないためです。</span><span class="sxs-lookup"><span data-stu-id="c8832-192">This is because we don't have a separate sentinel for the null.</span></span>

<span data-ttu-id="c8832-193">•   所有型の継承マッピングはサポートされていませんが、異なる所有型と同じ継承階層の 2 つのリーフ型をマップすることはできます。</span><span class="sxs-lookup"><span data-stu-id="c8832-193">•   No inheritance mapping support for owned types, but you should be able to map two leaf types of the same inheritance hierarchies as different owned types.</span></span> <span data-ttu-id="c8832-194">EF Core は、同じ階層に属することの理由にはなりません。</span><span class="sxs-lookup"><span data-stu-id="c8832-194">EF Core will not reason about the fact that they are part of the same hierarchy.</span></span>

#### <a name="main-differences-with-ef6s-complex-types"></a><span data-ttu-id="c8832-195">EF6 の複合型との主な違い</span><span class="sxs-lookup"><span data-stu-id="c8832-195">Main differences with EF6's complex types</span></span>

<span data-ttu-id="c8832-196">•   テーブル分割は省略可能です。つまり、所有型のまま、必要に応じて別のテーブルにマップすることができます。</span><span class="sxs-lookup"><span data-stu-id="c8832-196">•   Table splitting is optional, i.e. they can optionally be mapped to a separate table and still be owned types.</span></span>

<span data-ttu-id="c8832-197">•   他のエンティティを参照することができます (つまり、他の非所有型との関係で依存側として機能することができます)。</span><span class="sxs-lookup"><span data-stu-id="c8832-197">•   They can reference other entities (i.e. they can act as the dependent side on relationships to other non-owned types).</span></span>


## <a name="additional-resources"></a><span data-ttu-id="c8832-198">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="c8832-198">Additional resources</span></span>

-   <span data-ttu-id="c8832-199">**Martin Fowler。ValueObject パターン**
    [*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)</span><span class="sxs-lookup"><span data-stu-id="c8832-199">**Martin Fowler. ValueObject pattern**
[*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)</span></span>

-   <span data-ttu-id="c8832-200">**Eric Evans。Domain-Driven Design: Tackling Complexity in the Heart of Software (ドメイン駆動設計: ソフトウェア中心部の複雑さへの取り組み)。**</span><span class="sxs-lookup"><span data-stu-id="c8832-200">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software.**</span></span> <span data-ttu-id="c8832-201">(書籍、値オブジェクトについての記載あり) [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span><span class="sxs-lookup"><span data-stu-id="c8832-201">(Book; includes a discussion of value objects) [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span></span>

-   <span data-ttu-id="c8832-202">**Vaughn Vernon。ドメイン駆動型設計の実装**</span><span class="sxs-lookup"><span data-stu-id="c8832-202">**Vaughn Vernon. Implementing Domain-Driven Design.**</span></span> <span data-ttu-id="c8832-203">(書籍、値オブジェクトについての記載あり) [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span><span class="sxs-lookup"><span data-stu-id="c8832-203">(Book; includes a discussion of value objects) [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span></span>

-   <span data-ttu-id="c8832-204">**シャドウ プロパティ**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span><span class="sxs-lookup"><span data-stu-id="c8832-204">**Shadow Properties**
[*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span></span>

-   <span data-ttu-id="c8832-205">**複合型と値オブジェクト**。</span><span class="sxs-lookup"><span data-stu-id="c8832-205">**Complex types and/or value objects**.</span></span> <span data-ttu-id="c8832-206">EF Core GitHub リポジトリのディスカッション ([問題] タブ) [*https://github.com/aspnet/EntityFramework/issues/246*](https://github.com/aspnet/EntityFramework/issues/246)</span><span class="sxs-lookup"><span data-stu-id="c8832-206">Discussion in the EF Core GitHub repo (Issues tab) [*https://github.com/aspnet/EntityFramework/issues/246*](https://github.com/aspnet/EntityFramework/issues/246)</span></span>

-   <span data-ttu-id="c8832-207">**ValueObject.cs.**</span><span class="sxs-lookup"><span data-stu-id="c8832-207">**ValueObject.cs.**</span></span> <span data-ttu-id="c8832-208">eShopOnContainers の基底値オブジェクト クラス。</span><span class="sxs-lookup"><span data-stu-id="c8832-208">Base value object class in eShopOnContainers.</span></span>
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs)

-   <span data-ttu-id="c8832-209">**Address クラス。**</span><span class="sxs-lookup"><span data-stu-id="c8832-209">**Address class.**</span></span> <span data-ttu-id="c8832-210">eShopOnContainers の値オブジェクト クラスのサンプル。</span><span class="sxs-lookup"><span data-stu-id="c8832-210">Sample value object class in eShopOnContainers.</span></span>
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs)



>[!div class="step-by-step"]
<span data-ttu-id="c8832-211">[前へ] (seedwork-domain-model-base-classes-interfaces.md) [次へ] (enumeration-classes-over-enum-types.md)</span><span class="sxs-lookup"><span data-stu-id="c8832-211">[Previous] (seedwork-domain-model-base-classes-interfaces.md) [Next] (enumeration-classes-over-enum-types.md)</span></span>
