---
title: 列挙型ではなく列挙型クラスを使用する
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | 列挙型ではなく列挙型クラスを使用する
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 1b2569caa7e7a6a899a6765d2e39d0fff8e37e2f
ms.sourcegitcommit: 6c480773ae896f45af4671fb3e26611a50e4dd81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2018
ms.locfileid: "35251195"
---
# <a name="using-enumeration-classes-instead-of-enum-types"></a><span data-ttu-id="a6e0f-103">列挙型ではなく列挙型クラスを使用する</span><span class="sxs-lookup"><span data-stu-id="a6e0f-103">Using enumeration classes instead of enum types</span></span>

<span data-ttu-id="a6e0f-104">[列挙型](../../../../docs/csharp/language-reference/keywords/enum.md) (省略形も同じ *列挙型*) は、整数型を包む薄い言語ラッパーです。</span><span class="sxs-lookup"><span data-stu-id="a6e0f-104">[Enumerations](../../../../docs/csharp/language-reference/keywords/enum.md) (or *enum types* for short) are a thin language wrapper around an integral type.</span></span> <span data-ttu-id="a6e0f-105">閉じた値のセットから 1 つの値を格納するときに、列挙型の使用を制限することができます。</span><span class="sxs-lookup"><span data-stu-id="a6e0f-105">You might want to limit their use to when you are storing one value from a closed set of values.</span></span> <span data-ttu-id="a6e0f-106">サイズ (小、中、大) に基づく分類は良い一例です。</span><span class="sxs-lookup"><span data-stu-id="a6e0f-106">Classification based on sizes (small, medium, large) is a good example.</span></span> <span data-ttu-id="a6e0f-107">制御フローまたはより堅牢な抽象化のために列挙型を使用すると、[コードの臭い](http://deviq.com/code-smells/)になることがあります。</span><span class="sxs-lookup"><span data-stu-id="a6e0f-107">Using enums for control flow or more robust abstractions can be a [code smell](http://deviq.com/code-smells/).</span></span> <span data-ttu-id="a6e0f-108">このような用法は、列挙型の値を検査する多くの制御フロー ステートメントでは脆弱なコードにつながります。</span><span class="sxs-lookup"><span data-stu-id="a6e0f-108">This type of usage leads to fragile code with many control flow statements checking values of the enum.</span></span>

<span data-ttu-id="a6e0f-109">代わりに、オブジェクト指向言語の豊富な機能をすべて使用できる列挙型クラスを作成する方法があります。</span><span class="sxs-lookup"><span data-stu-id="a6e0f-109">Instead, you can create Enumeration classes that enable all the rich features of an object-oriented language.</span></span>

<span data-ttu-id="a6e0f-110">ただし、これは重要な話題ではなく、多くの場合は、好みに応じてわかりやすくするために通常の[列挙型](../../../../docs/csharp/language-reference/keywords/enum.md)を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="a6e0f-110">However, this isn't a critical topic and in many cases, for simplicity, you can still use regular [enum types](../../../../docs/csharp/language-reference/keywords/enum.md) if that's your preference.</span></span>

## <a name="implementing-an-enumeration-base-class"></a><span data-ttu-id="a6e0f-111">列挙型基底クラスの実装</span><span class="sxs-lookup"><span data-stu-id="a6e0f-111">Implementing an Enumeration base class</span></span>

<span data-ttu-id="a6e0f-112">eShopOnContainers 内の注文マイクロサービスは、次の例のように、列挙型基底クラスの実装サンプルを提供しています。</span><span class="sxs-lookup"><span data-stu-id="a6e0f-112">The ordering microservice in eShopOnContainers provides a sample Enumeration base class implementation, as shown in the following example:</span></span>

```csharp
public abstract class Enumeration : IComparable
{
    public string Name { get; }
    public int Id { get; }

    protected Enumeration()
    {
    }

    protected Enumeration(int id, string name)
    {
        Id = id;
        Name = name;
    }

    public override string ToString()
    {
        return Name;
    }

    public static IEnumerable<T> GetAll<T>() where T : Enumeration, new()
    {
        var type = typeof(T);
        var fields = type.GetTypeInfo().GetFields(BindingFlags.Public |
            BindingFlags.Static |
            BindingFlags.DeclaredOnly);
        foreach (var info in fields)
        {
            var instance = new T();
            var locatedValue = info.GetValue(instance) as T;
            if (locatedValue != null)
            {
                yield return locatedValue;
            }
        }
    }

    public override bool Equals(object obj)
    {
        var otherValue = obj as Enumeration;
        if (otherValue == null)
        {
            return false;
        }
        var typeMatches = GetType().Equals(obj.GetType());
        var valueMatches = Id.Equals(otherValue.Id);
        return typeMatches && valueMatches;
    }

    public int CompareTo(object other)
    {
        return Id.CompareTo(((Enumeration)other).Id);
    }

    // Other utility methods ...
}
```

<span data-ttu-id="a6e0f-113">次の CardType 列挙型クラスと同様に、このクラスを任意のエンティティまたは値オブジェクトの型として使用できます。</span><span class="sxs-lookup"><span data-stu-id="a6e0f-113">You can use this class as a type in any entity or value object, as for the following CardType Enumeration class:</span></span>

```csharp
public class CardType : Enumeration
{
    public static CardType Amex = new CardType(1, "Amex");
    public static CardType Visa = new CardType(2, "Visa");
    public static CardType MasterCard = new CardType(3, "MasterCard");

    protected CardType() { }

    public CardType(int id, string name)
        : base(id, name)
    {
    }

    public static IEnumerable<CardType> List()
    {
        return new[] { Amex, Visa, MasterCard };
    }
    // Other util methods
}
```

## <a name="additional-resources"></a><span data-ttu-id="a6e0f-114">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="a6e0f-114">Additional resources</span></span>

-   <span data-ttu-id="a6e0f-115">**列挙型は悪 — 更新**
    [*https://www.planetgeek.ch/2009/07/01/enums-are-evil/*](https://www.planetgeek.ch/2009/07/01/enums-are-evil/)</span><span class="sxs-lookup"><span data-stu-id="a6e0f-115">**Enum’s are evil—update**
[*https://www.planetgeek.ch/2009/07/01/enums-are-evil/*](https://www.planetgeek.ch/2009/07/01/enums-are-evil/)</span></span>

-   <span data-ttu-id="a6e0f-116">**Daniel Hardman。列挙型で広がる病気 — そしてその治療方法**
    [*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)</span><span class="sxs-lookup"><span data-stu-id="a6e0f-116">**Daniel Hardman. How Enums Spread Disease — And How To Cure It**
[*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)</span></span>

-   <span data-ttu-id="a6e0f-117">**Jimmy Bogard。列挙型クラス**
    [*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)</span><span class="sxs-lookup"><span data-stu-id="a6e0f-117">**Jimmy Bogard. Enumeration classes**
[*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)</span></span>

-   <span data-ttu-id="a6e0f-118">**Steve Smith。C# の列挙型の代替**
    [*https://ardalis.com/enum-alternatives-in-c*](https://ardalis.com/enum-alternatives-in-c)</span><span class="sxs-lookup"><span data-stu-id="a6e0f-118">**Steve Smith. Enum Alternatives in C#**
[*https://ardalis.com/enum-alternatives-in-c*](https://ardalis.com/enum-alternatives-in-c)</span></span>

-   <span data-ttu-id="a6e0f-119">**Enumeration.cs。**</span><span class="sxs-lookup"><span data-stu-id="a6e0f-119">**Enumeration.cs.**</span></span> <span data-ttu-id="a6e0f-120">eShopOnContainers の基底列挙型クラス[*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)</span><span class="sxs-lookup"><span data-stu-id="a6e0f-120">Base Enumeration class in eShopOnContainers [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)</span></span>

-   <span data-ttu-id="a6e0f-121">**CardType.cs**。</span><span class="sxs-lookup"><span data-stu-id="a6e0f-121">**CardType.cs**.</span></span> <span data-ttu-id="a6e0f-122">eShopOnContainers のサンプル列挙型クラス。</span><span class="sxs-lookup"><span data-stu-id="a6e0f-122">Sample Enumeration class in eShopOnContainers.</span></span>
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs)


>[!div class="step-by-step"]
<span data-ttu-id="a6e0f-123">[Previous] (implement-value-objects.md) [Next] (domain-model-layer-validations.md)</span><span class="sxs-lookup"><span data-stu-id="a6e0f-123">[Previous] (implement-value-objects.md) [Next] (domain-model-layer-validations.md)</span></span>
