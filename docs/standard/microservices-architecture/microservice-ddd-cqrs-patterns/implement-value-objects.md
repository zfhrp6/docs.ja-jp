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
# <a name="implementing-value-objects"></a>値オブジェクトを実装します。

エンティティと集計については、前のセクションで既に説明した、id はエンティティの基本的なです。 ただし、多数のオブジェクトとデータ項目にある、id、および値オブジェクトなど、追跡 id を必要としないシステムです。

値オブジェクトには、他のエンティティを参照できます。 など、1 つのポイントから取得する方法について説明するルートを生成するアプリケーションでそのルート オブジェクトの値になります。 特定のルート上のポイントのスナップショットになりますが、内部的に参照するエンティティと市区町村、道路などもこの提案されたルートは、id はありません。

図 9. ~ 13. では、注文集計内のアドレス値オブジェクトを示します。

![](./media/image14.png)

**図 9. ~ 13.**です。 順序の集計内のオブジェクトの値に対応します。

図 9-13 に示すように、複数の属性はエンティティが通常で構成されます。 たとえば、順序を id を持つエンティティとしてモデル化し、OrderId、OrderDate、OrderItems などの属性のセットの内部で構成されます。しかし、アドレスは、複合型の値だけから成る国、番地、市区町村などのモデル化し、値のオブジェクトとして扱われます必要があります。

## <a name="important-characteristics-of-value-objects"></a>値オブジェクトの重要な特性

値オブジェクトの 2 つの主な特徴があります。

-   Id があるありません。

-   変更可能なことはできません。

1 番目の特性は既に説明しました。 不変性は、重要な要件です。 値オブジェクトの値、オブジェクトを作成した後に変更可能なことがあります。 そのため、オブジェクトを作成するとき、必要な値を指定する必要がありますが、オブジェクトの有効期間中に変更することを許可する必要がありません。

値オブジェクトを使用すると、変更できない性質により、パフォーマンスの特定のテクニックを実行することができます。 これは、システムで特に同じ値を持つたくさんある数千の値のオブジェクトのインスタンス、します。 変更できない、本来を再利用できること。その値が同じでありの id がないために、交換可能なオブジェクトが存在することができます。 この最適化の種類にできるの違いは、実行速度が遅いソフトウェアとソフトウェア良好なパフォーマンスをことがあります。 もちろん、このような場合は、アプリケーション環境と展開のコンテキストに依存します。

## <a name="value-object-implementation-in-c"></a>C＃での値オブジェクトの実装

実装では、観点から (からのオブジェクトの値は、id に基づいている必要がありますいない) すべての属性とその他の基本的な特性の比較に基づいてに等しいかどうかのような基本的なユーティリティ メソッドを持つ値オブジェクトの基本クラスことができます。 次の例では、eShopOnContainers から順序マイクロ サービスで使用される、値オブジェクトの基本クラスを示します。

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

次の例に示すように、アドレス値オブジェクトと同様、実際の値オブジェクトを実装するときにこのクラスを使用できます。

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

## <a name="hiding-the-identity-characteristic-when-using-ef-core-to-persist-value-objects"></a>EF コアを使用して値オブジェクトを保持する場合、識別特性を非表示にします。

現在のバージョン (EF コア 1.1) では使用できないことを EF コアを使用する場合、制限[複合型](https://docs.microsoft.com/de-de/dotnet/api/system.componentmodel.dataannotations.schema.complextypeattribute?view=netframework-4.7)EF で定義されている 6.x です。 そのため、EF エンティティとして、オブジェクトの値を格納する必要があります。 ただし、クリア、id がオブジェクトの値が含まれるモデルで重要でないことを行うようには、その ID を非表示にできます。 ID を非表示にする、シャドウ プロパティとして、ID を使用することです。 その構成モデルの ID を非表示に設定されているためインフラストラクチャ レベルで、ドメイン モデルに対して透過的になり、インフラストラクチャ実装は、今後変更可能性があります。

EShopOnContainers での EF のコア インフラストラクチャで必要な非表示の ID インフラストラクチャ プロジェクトで Fluent API を使用して DbContext レベルでは、次のように実装されます。

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

そのため、ID が、ドメイン モデルの観点から、非表示、今後は、値オブジェクトのインフラストラクチャでしたも実装する複合型または別の方法として。

## <a name="additional-resources"></a>その他の技術情報

-   **Martin Fowler。ValueObject パターン**
    [*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)

-   **Eric Evans。ドメインに基づく設計: は Tackling Complexity in the Heart of Software です。** (予約値オブジェクトの説明を含む)。[ *https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

-   **Vaughn Vernon。ドメインに基づく設計の実装です。** (予約値オブジェクトの説明を含む)。[ *https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)

-   **プロパティをシャドウ**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)

-   **複合型および値オブジェクト**です。 EF コア GitHub リポジトリ ([問題] タブ) でディスカッション[ *https://github.com/aspnet/EntityFramework/issues/246*](https://github.com/aspnet/EntityFramework/issues/246)

-   **ValueObject.cs です。** オブジェクト クラスを基本値 eShopOnContainers にします。
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs)

-   **クラスに対応します。** サンプル値のオブジェクト クラス eShopOnContainers です。
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs)


>[!div class="step-by-step"]
[前](seedwork-domain-model-base-classes-interfaces.md) [次へ] (列挙型のクラスの over-enum-types.md)
