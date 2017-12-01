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
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a>Seedwork (再利用可能な基本クラスと、ドメイン モデルのインターフェイス)

ソリューション フォルダーに含まれる、 *SeedWork*フォルダーです。 *SeedWork*フォルダーには、ドメインのエンティティおよび値オブジェクトをベースとして使用できるカスタムの基本クラスが含まれています。 各ドメインのオブジェクト クラスで、冗長なコードはありませんので、これらの基本クラスを使用します。 これらの型クラスのフォルダーと呼びます*SeedWork*などのメカニズムではありませんし*Framework*です。 呼び出された*SeedWork*フォルダーには、フレームワークは見なされません本当に再利用可能なクラスの小さなサブセットのみが含まれているためです。 *Seedwork*用語によって導入[Michael の受信可能方向](http://www.artima.com/forums/flat.jsp?forum=106&thread=8826)が増幅し、 [Martin ファウラー](https://martinfowler.com/bliki/Seedwork.html)共通、SharedKernel、フォルダーの名前もでしたが、または類似します。

図 9-12 では、順序付けのマイクロ サービスにドメイン モデルの seedwork を形成するクラスを示します。 エンティティ、ValueObject、および列挙体と同様に、いくつかのカスタムの基本クラスとインターフェイスのいくつかあります。 (IRepository および IUnitOfWork) これらのインターフェイスを実装する必要のあるについて、インフラストラクチャ レイヤーに通知します。 これらのインターフェイスは、アプリケーション レイヤーからの依存関係の挿入も使われます。

![](./media/image13.PNG)

**図 9-12**です。 サンプルは、ドメイン モデル"seedwork"基本クラスとインターフェイスの設定

これは、多くの開発者は、プロジェクト、正式なフレームワークではない間で共有するコピーと貼り付けを再利用の型です。 任意のレイヤーまたはライブラリで seedworks ことができます。 ただし、クラスとインターフェイスのセットは、十分な大きさを取得、可能性がある場合は、1 つのクラス ライブラリを作成します。

## <a name="the-custom-entity-base-class"></a>カスタム エンティティの基本クラス

次のコードは、エンティティの基本クラスの例であり、エンティティ ID など、任意のドメイン エンティティで同じ方法を使用できるコードを配置する[等値演算子](https://msdn.microsoft.com/en-us/library/c35t2ffz.aspx), などです。

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

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a>ドメイン モデル レイヤーにおいてリポジトリ コントラクト (インターフェイス)

リポジトリのコントラクトは、各集計に使用する、リポジトリのコントラクト要件を表現する .NET インターフェイスだけです。 ドメイン モデル内で EF コア コード、またはその他のインフラストラクチャの依存関係、およびコードを使用、自体のリポジトリを実装する必要がありません。リポジトリでは、定義するインターフェイスを実装する必要がありますだけです。

この実習 (ドメイン モデル レイヤーにおいてリポジトリ インターフェイスを配置すること) に関連するパターンは、インターフェイスの区切られたパターンです。 として[説明](http://www.martinfowler.com/eaaCatalog/separatedInterface.html)で Martin ファウラー"を 1 つのインターフェイスを定義する区切りインターフェイスを使用してパッケージが、別の実装します。 この方法インターフェイスへの依存関係が必要なクライアントがありますの実装では、完全に注意してください。"

ドメイン モデルで定義されている要件への依存関係がインフラストラクチャ/永続化に直接依存されませんが、アプリケーション層 (ここでは、マイクロ サービスの Web API プロジェクト) を有効に区切られたインターフェイス パターンに従うレイヤーです。 依存関係の挿入を使用して、インフラストラクチャで実装されると、実装を分離するさらに、永続性レイヤーのリポジトリを使用しています。

たとえば、IOrderRepository インターフェイスで次の例では、OrderRepository クラスは、インフラストラクチャ レイヤーで実装する必要があります、どのような操作を定義します。 アプリケーションの現在の実装で、コードはクエリは、分割次 CQS アプローチと注文への更新が実装されていないため、データベースに注文を追加するだけが必要です。

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

## <a name="additional-resources"></a>その他の技術情報

-   **Martin Fowler。分離されたインターフェイスです。** 
     [ *http://www.martinfowler.com/eaaCatalog/separatedInterface.html*](http://www.martinfowler.com/eaaCatalog/separatedInterface.html%20)


>[!div class="step-by-step"]
[前](net-コア-マイクロ サービスのドメイン-model.md) [次へ] (実装値 objects.md)
