---
title: "列挙型ではなく列挙型クラスを使用します。"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |列挙型ではなく列挙型クラスを使用します。"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 1745198720fd12a9d26aab2d2afb2c5dd6b6b49d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="using-enumeration-classes-instead-of-enum-types"></a><span data-ttu-id="07853-104">列挙型ではなく列挙型クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="07853-104">Using Enumeration classes instead of enum types</span></span>

<span data-ttu-id="07853-105">[列挙体](https://msdn.microsoft.com/en-us/library/sbbt4032.aspx)(*列挙型*を短い) は整数型のラッパー シン言語。</span><span class="sxs-lookup"><span data-stu-id="07853-105">[Enumerations](https://msdn.microsoft.com/en-us/library/sbbt4032.aspx) (*enums* for short) are a thin language wrapper around an integral type.</span></span> <span data-ttu-id="07853-106">閉じられた一連の値から 1 つの値を格納する場合に、使用を制限する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="07853-106">You might want to limit their use to when you are storing one value from a closed set of values.</span></span> <span data-ttu-id="07853-107">性別 (たとえば、male, female、不明な)、またはサイズ (S、M、L、XL) に基づく分類は、良い例です。</span><span class="sxs-lookup"><span data-stu-id="07853-107">Classification based on gender (for example, male, female, unknown), or sizes (S, M, L, XL) are good examples.</span></span> <span data-ttu-id="07853-108">制御フローまたはより堅牢な抽象化の列挙型を使用することができます、[コードの匂い](http://deviq.com/code-smells/)です。</span><span class="sxs-lookup"><span data-stu-id="07853-108">Using enums for control flow or more robust abstractions can be a [code smell](http://deviq.com/code-smells/).</span></span> <span data-ttu-id="07853-109">この種類の使用状況は、多くの制御フロー ステートメントの列挙型の値のチェックで脆弱なコードにつながります。</span><span class="sxs-lookup"><span data-stu-id="07853-109">This type of usage will lead to fragile code with many control flow statements checking values of the enum.</span></span>

<span data-ttu-id="07853-110">代わりに、オブジェクト指向言語のすべての機能豊富な機能を有効にする列挙型クラスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="07853-110">Instead, you can create Enumeration classes that enable all the rich features of an object-oriented language.</span></span> <span data-ttu-id="07853-111">ただし、これは重大な問題ではありません多くの場合、わかりやすくするため、することができますもを使用して標準列挙型、基本設定である場合。</span><span class="sxs-lookup"><span data-stu-id="07853-111">However, this is not a critical issue and in many cases, for simplicity, you can still use regular enums if that is your preference.</span></span>

## <a name="implementing-enumeration-classes"></a><span data-ttu-id="07853-112">列挙型クラスの実装</span><span class="sxs-lookup"><span data-stu-id="07853-112">Implementing Enumeration classes</span></span>

<span data-ttu-id="07853-113">EShopOnContainers で順序付けマイクロ サービスは、次の例で示すようにサンプル列挙基本クラスの実装を示します。</span><span class="sxs-lookup"><span data-stu-id="07853-113">The ordering microservice in eShopOnContainers provides a sample Enumeration base class implementation, as shown in the following example:</span></span>

```csharp
public abstract class Enumeration : IComparable
{
    public string Name { get; private set; }
    public int Id { get; private set; }

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

<span data-ttu-id="07853-114">このクラスは、次の CardType 列挙型クラスに関する、エンティティまたは値オブジェクト内の型として使用できます。</span><span class="sxs-lookup"><span data-stu-id="07853-114">You can use this class as a type in any entity or value object, as for the following CardType Enumeration class.</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="07853-115">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="07853-115">Additional resources</span></span>

-   <span data-ttu-id="07853-116">**列挙型の evil-更新**
    [*http://www.planetgeek.ch/2009/07/01/enums-are-evil/*](http://www.planetgeek.ch/2009/07/01/enums-are-evil/)</span><span class="sxs-lookup"><span data-stu-id="07853-116">**Enum’s are evil—update**
[*http://www.planetgeek.ch/2009/07/01/enums-are-evil/*](http://www.planetgeek.ch/2009/07/01/enums-are-evil/)</span></span>

-   <span data-ttu-id="07853-117">**Daniel Hardman です。列挙型マップする方法病気 — これを解決する方法と**
    [*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)</span><span class="sxs-lookup"><span data-stu-id="07853-117">**Daniel Hardman. How Enums Spread Disease — And How To Cure It**
[*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)</span></span>

-   <span data-ttu-id="07853-118">**Jimmy Bogard。列挙クラス**
    [*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)</span><span class="sxs-lookup"><span data-stu-id="07853-118">**Jimmy Bogard. Enumeration classes**
[*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)</span></span>

-   <span data-ttu-id="07853-119">**Steve Smith です。C# での Enum 代替**
    [*http://ardalis.com/enum-alternatives-in-c*](http://ardalis.com/enum-alternatives-in-c)</span><span class="sxs-lookup"><span data-stu-id="07853-119">**Steve Smith. Enum Alternatives in C#**
[*http://ardalis.com/enum-alternatives-in-c*](http://ardalis.com/enum-alternatives-in-c)</span></span>

-   <span data-ttu-id="07853-120">**Enumeration.cs です。**</span><span class="sxs-lookup"><span data-stu-id="07853-120">**Enumeration.cs.**</span></span> <span data-ttu-id="07853-121">基本 eShopOnContainers で列挙型クラス[ *https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)</span><span class="sxs-lookup"><span data-stu-id="07853-121">Base Enumeration class in eShopOnContainers [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)</span></span>

-   <span data-ttu-id="07853-122">**CardType.cs**です。</span><span class="sxs-lookup"><span data-stu-id="07853-122">**CardType.cs**.</span></span> <span data-ttu-id="07853-123">EShopOnContainers サンプル列挙型クラス。</span><span class="sxs-lookup"><span data-stu-id="07853-123">Sample Enumeration class in eShopOnContainers.</span></span>
    [<span data-ttu-id="07853-124">*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*</span><span class="sxs-lookup"><span data-stu-id="07853-124">*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*</span></span>](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs)


>[!div class="step-by-step"]
<span data-ttu-id="07853-125">[前](実装の値-objects.md) [次へ] (ドメインのモデルのレイヤー-validations.md)</span><span class="sxs-lookup"><span data-stu-id="07853-125">[Previous] (implement-value-objects.md) [Next] (domain-model-layer-validations.md)</span></span>
