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
# <a name="using-enumeration-classes-instead-of-enum-types"></a>列挙型ではなく列挙型クラスを使用します。

[列挙体](https://msdn.microsoft.com/en-us/library/sbbt4032.aspx)(*列挙型*を短い) は整数型のラッパー シン言語。 閉じられた一連の値から 1 つの値を格納する場合に、使用を制限する可能性があります。 性別 (たとえば、male, female、不明な)、またはサイズ (S、M、L、XL) に基づく分類は、良い例です。 制御フローまたはより堅牢な抽象化の列挙型を使用することができます、[コードの匂い](http://deviq.com/code-smells/)です。 この種類の使用状況は、多くの制御フロー ステートメントの列挙型の値のチェックで脆弱なコードにつながります。

代わりに、オブジェクト指向言語のすべての機能豊富な機能を有効にする列挙型クラスを作成できます。 ただし、これは重大な問題ではありません多くの場合、わかりやすくするため、することができますもを使用して標準列挙型、基本設定である場合。

## <a name="implementing-enumeration-classes"></a>列挙型クラスの実装

EShopOnContainers で順序付けマイクロ サービスは、次の例で示すようにサンプル列挙基本クラスの実装を示します。

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

このクラスは、次の CardType 列挙型クラスに関する、エンティティまたは値オブジェクト内の型として使用できます。

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

## <a name="additional-resources"></a>その他の技術情報

-   **列挙型の evil-更新**
    [*http://www.planetgeek.ch/2009/07/01/enums-are-evil/*](http://www.planetgeek.ch/2009/07/01/enums-are-evil/)

-   **Daniel Hardman です。列挙型マップする方法病気 — これを解決する方法と**
    [*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)

-   **Jimmy Bogard。列挙クラス**
    [*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)

-   **Steve Smith です。C# での Enum 代替**
    [*http://ardalis.com/enum-alternatives-in-c*](http://ardalis.com/enum-alternatives-in-c)

-   **Enumeration.cs です。** 基本 eShopOnContainers で列挙型クラス[ *https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)

-   **CardType.cs**です。 EShopOnContainers サンプル列挙型クラス。
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs)


>[!div class="step-by-step"]
[前](実装の値-objects.md) [次へ] (ドメインのモデルのレイヤー-validations.md)
