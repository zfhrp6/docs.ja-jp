---
title: Seedwork (ドメイン モデルの再利用可能な基底クラスとインターフェイス)
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | Seedwork (ドメイン モデルの再利用可能な基底クラスとインターフェイス)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.openlocfilehash: 21f502d74aab10b306e350ee831583f06b394dc7
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105104"
---
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a>Seedwork (ドメイン モデルの再利用可能な基底クラスとインターフェイス)

ソリューション フォルダーには、*SeedWork* フォルダーが含まれています。 *SeedWork* フォルダー内にあるカスタム基底クラスは、ドメイン エンティティおよび値オブジェクトの基礎として使用できます。 これらの基底クラスを使用すると、各ドメインのオブジェクト クラスで冗長なコードがなくなります。 これらのタイプのクラス用のフォルダーは、*Framework* のような名前ではなく、*SeedWork* という名前になっています。 *SeedWork* という名前になっているのは、このフォルダーには再利用可能なクラスのほんの一部しか含まれておらず、実際にはフレームワークと見なすことができないためです。 *Seedwork* は、[Michael Feathers](https://www.artima.com/forums/flat.jsp?forum=106&thread=8826) が発表し、[Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) が普及させた用語ですが、Common や SharedKernel といった名前で呼ばれる場合もあります。

図 9-12 は、注文マイクロサービスのドメイン モデルの SeedWork を構成するクラスを示しています。 カスタム基底クラス (Entity、ValueObject、Enumeration など) とインターフェイスがいくつか含まれています。 これらのインターフェイス (IRepository と IUnitOfWork) は、実装する必要があるものをインフラストラクチャ レイヤーに通知します。 また、これらのインターフェイスは、アプリケーション レイヤーから依存関係の挿入を通じて使用されます。

![](./media/image13.PNG)

**図 9-12**. ドメイン モデル "SeedWork" の基底クラスとインターフェイスのサンプル セット

これは、コピーと貼り付けによって再利用するタイプのもので、多くの開発者によってプロジェクト間で共有されます。正式なフレームワークではありません。 SeedWork は、どのレイヤーやライブラリでも使用できます。 ただし、クラスとインターフェイスのセットが十分に大きくなったら、単一のクラス ライブラリを作成するのがよいでしょう。

## <a name="the-custom-entity-base-class"></a>カスタム Entity 基底クラス

次のコードは、Entity 基底クラスの例です。このクラスでは、任意のドメイン エンティティ (エンティティ ID、[等値演算子](/cpp/cpp/equality-operators-equal-equal-and-exclpt-equal)、エンティティごとのドメイン イベント リストなど) が同様の方法で使用できるコードを配置できます。

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

エンティティごとのドメイン イベント リストを使用する以前のコードについては、次のセクションでドメイン イベントを取り上げるときに説明します。 

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a>ドメイン モデル レイヤーのリポジトリ コントラクト (インターフェイス)

リポジトリ コントラクトは、各集計に使用されるリポジトリのコントラクト要件を示すシンプルな .NET インターフェイスです。 

リポジトリ自体と EF コア コード、または他の任意のインフラストラクチャの依存関係やコード (Linq や SQL など) は、ドメイン モデル内に実装してはなりません。リポジトリは、ユーザー定義のインターフェイスのみを実装する必要があります。 

この手法 (リポジトリ インターフェイスをドメイン モデル レイヤーに配置する手法) に関連するパターンが、インターフェイスの分離 パターンです。 Martin Fowler は、次のように[説明](https://www.martinfowler.com/eaaCatalog/separatedInterface.html)しています。"インターフェイスの分離を使用して、あるインターフェイスをあるパッケージに定義します。ただし、その実装は、別のパッケージで行います。 これにより、このインターフェイスへの依存関係が必要なクライアントは、実装を全く意識せずにすむようになります。"

インターフェイスの分離パターンに従うと、アプリケーション レイヤー (この場合はマイクロサービスの Web API プロジェクト) は、ドメイン モデルで定義された要件に対する依存関係を持つことができます。ただし、インフラストラクチャ/ 永続化レイヤーに対する直接の依存関係を持つことはできません。 また、依存関係の挿入を使用すると、リポジトリを使用してインフラストラクチャ/永続化レイヤーに実装された実装を分離できます。

たとえば、IOrderRepository インターフェイスを使用する次の例では、OrderRepository クラスがインフラストラクチャ レイヤーで実装する必要のある操作が定義されています。 アプリケーションの現在の実装では、簡略化された CQRS アプローチに従ってクエリが分割されているため、コードは、データベースに注文を追加するか、またはデータベースの注文を更新する必要があります。

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

## <a name="additional-resources"></a>その他の技術情報

-   **Martin Fowler。インターフェイスの分離。**
    [*https://www.martinfowler.com/eaaCatalog/separatedInterface.html*](https://www.martinfowler.com/eaaCatalog/separatedInterface.html)


>[!div class="step-by-step"]
[前へ](net-core-microservice-domain-model.md)
[次へ](implement-value-objects.md)
