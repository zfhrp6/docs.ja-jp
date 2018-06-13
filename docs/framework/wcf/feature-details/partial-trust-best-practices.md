---
title: 部分信頼のベスト プラクティス
ms.date: 03/30/2017
ms.assetid: 0d052bc0-5b98-4c50-8bb5-270cc8a8b145
ms.openlocfilehash: fca975ff4216384b970535273511eb07cd6ded68
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497270"
---
# <a name="partial-trust-best-practices"></a>部分信頼のベスト プラクティス
このトピックでは、部分信頼環境で Windows Communication Foundation (WCF) を実行する場合のベスト プラクティスについて説明します。  
  
## <a name="serialization"></a>シリアル化  
 部分信頼アプリケーションで <xref:System.Runtime.Serialization.DataContractSerializer> を使用する場合は、次の方法を適用します。  
  
-   すべてのシリアル化可能な型は、`[DataContract]` 属性で明示的にマークする必要があります。 次の手法は、部分信頼環境ではサポートされていません。  
  
-   シリアル化するクラスを <xref:System.SerializableAttribute> でマークする。  
  
-   クラスでシリアル化プロセスを制御できるように <xref:System.Runtime.Serialization.ISerializable> インターフェイスを実装する。  
  
### <a name="using-datacontractserializer"></a>DataContractSerializer の使用  
  
-   `[DataContract]` 属性でマークされたすべての型は、パブリックである必要があります。 部分信頼環境では、非パブリック型はシリアル化できません。  
  
-   シリアル化できる `[DataContract]` 型のすべての `[DataContract]` メンバーは、パブリックである必要があります。 部分信頼環境では、非パブリック `[DataMember]` 型はシリアル化できません。  
  
-   `OnSerializing`、`OnSerialized`、`OnDeserializing`、`OnDeserialized` などのシリアル化イベントを処理するメソッドは、パブリックとして宣言する必要があります。 ただし、明示的および暗黙的な <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%28System.Object%29> の実装は、いずれもサポートされています。  
  
-   `[DataContract]` は、逆シリアル化の間に新しくインスタンス化されたオブジェクトのコンストラクターを呼び出さないため、<xref:System.Security.AllowPartiallyTrustedCallersAttribute> でマークされて、アセンブリで実装された <xref:System.Runtime.Serialization.DataContractSerializer> 型は、型コンストラクターでセキュリティ関連の操作を実行することはできません。 特に、`[DataContract]` 型では、次の一般的なセキュリティ手法の使用を避ける必要があります。  
  
-   型のコンストラクターを内部またはプライベートにすることにより、部分信頼アクセスを制限する。  
  
-   型のコンストラクターに `[LinkDemand]` を追加することにより、型へのアクセスを制限する。  
  
-   オブジェクトが正常にインスタンス化されたため、コンストラクターが強制するチェックがすべて正常に終了したと仮定する。  
  
### <a name="using-ixmlserializable"></a>IXmlSerializable の使用  
 <xref:System.Xml.Serialization.IXmlSerializable> を実装し、<xref:System.Runtime.Serialization.DataContractSerializer> を使用してシリアル化される型に適用されるベスト プラクティスを次に示します。  
  
-   静的 <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> メソッドの実装は、`public` とする必要があります。  
  
-   <xref:System.Xml.Serialization.IXmlSerializable> インターフェイスを実装するインスタンス メソッドは、`public` とする必要があります。  
  
## <a name="using-wcf-from-fully-trusted-platform-code-that-allows-calls-from-partially-trusted-callers"></a>部分信頼の呼び出し元から呼び出せる完全信頼のプラットフォーム コードで WCF を使用する  
 WCF 部分信頼セキュリティ モデルでは、WCF のパブリック メソッドまたはプロパティの呼び出し元が、ホスト アプリケーションのコード アクセス セキュリティ (CAS) のコンテキストで実行されていることを前提としています。 WCF もその 1 つだけのアプリケーションのセキュリティ コンテキストはあるものと各<xref:System.AppDomain>でこのコンテキストが確立されると<xref:System.AppDomain>作成時の信頼されたホスト (への呼び出しなどによって<xref:System.AppDomain.CreateDomain%2A>または ASP.NET アプリケーション マネージャーによって)。  
  
 このセキュリティ モデルは、信頼性が "中" の ASP.NET アプリケーションで実行されているユーザー コードなど、追加の CAS アクセス許可をアサートできないユーザー記述のアプリケーションに適用されます。 ただし、完全に信頼されたプラットフォーム コード (グローバル アセンブリ キャッシュにインストールされてを部分信頼コードからの呼び出しを許可するサード パーティ アセンブリなど) 必要があるときの注意明示的に部分信頼アプリケーションに代わって WCF への呼び出しアプリケーション レベルのセキュリティの脆弱性を行わずに済みます。  
  
 完全信頼コードでは、現在のスレッドの CAS 権限のセットを変更することを避ける必要があります (を呼び出して<xref:System.Security.PermissionSet.Assert%2A>、 <xref:System.Security.PermissionSet.PermitOnly%2A>、または<xref:System.Security.PermissionSet.Deny%2A>) 部分信頼コードに代わって WCF Api を呼び出す前にします。 アプリケーション レベルのセキュリティ コンテキストに依存しないスレッド固有のアクセス許可コンテキストのアサート、拒否、または作成により、予期しない動作が発生することがあります。 アプリケーションによっては、この動作がアプリケーション レベルのセキュリティの脆弱性となることがあります。  
  
 発生する可能性が次のような状況を処理するスレッド固有のアクセス許可コンテキストを使用して WCF への呼び出しを準備する必要がありますコード:  
  
-   スレッド固有のセキュリティ コンテキストを処理の期間全体にわたっては保持できない場合があり、このときセキュリティの例外が発生する可能性があります。  
  
-   内部の WCF コードだけではなく、任意のユーザーが指定したコールバックは、呼び出しを開始すると最初の 1 つ以上の別のセキュリティ コンテキストで実行可能性があります。 次のようなコンテキストが含まれます。  
  
    -   アプリケーションのアクセス許可コンテキスト。  
  
    -   他のユーザー スレッドが現在実行中の有効期間中に WCF への呼び出しを使用して以前作成したスレッド固有のアクセス許可コンテキスト<xref:System.AppDomain>です。  
  
 WCF は、WCF のパブリック Api を呼び出す前に完全に信頼されたコンポーネントでこのようなアクセス許可がアサートされる場合を除き、部分信頼コードが完全信頼アクセス許可を取得できないことを保証します。 ただし、完全信頼をアサートした効果が特定のスレッド、操作、またはユーザー操作として隔離されることは保証されません。  
  
 <xref:System.Security.PermissionSet.Assert%2A>、<xref:System.Security.PermissionSet.PermitOnly%2A>、または <xref:System.Security.PermissionSet.Deny%2A> を呼び出すことにより、スレッド固有のアクセス許可コンテキストを作成しないことをお勧めします。 代わりに、<xref:System.Security.PermissionSet.Assert%2A>、<xref:System.Security.PermissionSet.Deny%2A>、または <xref:System.Security.PermissionSet.PermitOnly%2A> が不要となるように、アプリケーション自体に特権を付与するか、特権を拒否します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Xml.Serialization.IXmlSerializable>
