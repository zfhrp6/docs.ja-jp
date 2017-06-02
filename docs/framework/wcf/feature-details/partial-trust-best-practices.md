---
title: "部分信頼のベスト プラクティス | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0d052bc0-5b98-4c50-8bb5-270cc8a8b145
caps.latest.revision: 17
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 17
---
# 部分信頼のベスト プラクティス
このトピックでは、部分信頼環境で [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] を実行する場合のベスト プラクティスについて説明します。  
  
## シリアル化  
 部分信頼アプリケーションで <xref:System.Runtime.Serialization.DataContractSerializer> を使用する場合は、次の方法を適用します。  
  
-   すべてのシリアル化可能な型は、`[DataContract]` 属性で明示的にマークする必要があります。次の手法は、部分信頼環境ではサポートされていません。  
  
-   シリアル化するクラスを <xref:System.SerializableAttribute> でマークする。  
  
-   クラスでシリアル化プロセスを制御できるように <xref:System.Runtime.Serialization.ISerializable> インターフェイスを実装する。  
  
### DataContractSerializer の使用  
  
-   `[DataContract]` 属性でマークされたすべての型は、パブリックである必要があります。部分信頼環境では、非パブリック型はシリアル化できません。  
  
-   シリアル化できる `[DataContract]` 型のすべての `[DataContract]` メンバーは、パブリックである必要があります。部分信頼環境では、非パブリック `[DataMember]` 型はシリアル化できません。  
  
-   `OnSerializing`、`OnSerialized`、`OnDeserializing`、`OnDeserialized` などのシリアル化イベントを処理するメソッドは、パブリックとして宣言する必要があります。ただし、明示的および暗黙的な <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization%28System.Object%29> の実装は、いずれもサポートされています。  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> は、逆シリアル化の間に新しくインスタンス化されたオブジェクトのコンストラクターを呼び出さないため、<xref:System.Security.AllowPartiallyTrustedCallersAttribute> でマークされて、アセンブリで実装された `[DataContract]` 型は、型コンストラクターでセキュリティ関連の操作を実行することはできません。特に、`[DataContract]` 型では、次の一般的なセキュリティ手法の使用を避ける必要があります。  
  
-   型のコンストラクターを内部またはプライベートにすることにより、部分信頼アクセスを制限する。  
  
-   型のコンストラクターに `[LinkDemand]` を追加することにより、型へのアクセスを制限する。  
  
-   オブジェクトが正常にインスタンス化されたため、コンストラクターが強制するチェックがすべて正常に終了したと仮定する。  
  
### IXmlSerializable の使用  
 <xref:System.Xml.Serialization.IXmlSerializable> を実装し、<xref:System.Runtime.Serialization.DataContractSerializer> を使用してシリアル化される型に適用されるベスト プラクティスを次に示します。  
  
-   静的 <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> メソッドの実装は、`public` とする必要があります。  
  
-   <xref:System.Xml.Serialization.IXmlSerializable> インターフェイスを実装するインスタンス メソッドは、`public` とする必要があります。  
  
## 部分信頼の呼び出し元から呼び出せる完全信頼のプラットフォーム コードで WCF を使用する  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の部分信頼セキュリティ モデルでは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] パブリック メソッドまたはプロパティのすべての呼び出し元は、ホスト アプリケーションのコード アクセス セキュリティ \(CAS: Code Access Security\) コンテキストで実行されていることを前提としています。また、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] は、各 <xref:System.AppDomain> に対して存在するアプリケーション セキュリティ コンテキストが 1 つのみであり、このコンテキストが <xref:System.AppDomain.CreateDomain%2A> への呼び出しまたは、ASP.NET アプリケーション マネージャーなどの信頼されているホストにより、<xref:System.AppDomain> 作成時に確立されることを前提としています。  
  
 このセキュリティ モデルは、信頼性が "中" の ASP.NET アプリケーションで実行されているユーザー コードなど、追加の CAS アクセス許可をアサートできないユーザー記述のアプリケーションに適用されます。ただし、完全信頼のプラットフォーム コード \(たとえば、グローバル アセンブリ キャッシュにインストールされているサード パーティ アセンブリや、部分信頼コードからの呼び出しを受け入れるサード パーティ アセンブリなど\) は、アプリケーション レベルのセキュリティの脆弱性が発生しないよう、部分信頼アプリケーションに代わって [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を呼び出す場合に、明示的な注意を行う必要があります。  
  
 完全信頼コードでは、部分信頼コードに代わって [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] API を呼び出す前に、<xref:System.Security.PermissionSet.Assert%2A>、<xref:System.Security.PermissionSet.PermitOnly%2A>、または <xref:System.Security.PermissionSet.Deny%2A> を呼び出して、現在のスレッドの CAS アクセス許可セットを変更しないようにする必要があります。アプリケーション レベルのセキュリティ コンテキストに依存しないスレッド固有のアクセス許可コンテキストのアサート、拒否、または作成により、予期しない動作が発生することがあります。アプリケーションによっては、この動作がアプリケーション レベルのセキュリティの脆弱性となることがあります。  
  
 次のような状況の発生に対処するには、スレッド固有のアクセス許可コンテキストを使用して [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] を呼び出すコードを準備する必要があります。  
  
-   スレッド固有のセキュリティ コンテキストを処理の期間全体にわたっては保持できない場合があり、このときセキュリティの例外が発生する可能性があります。  
  
-   内部 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] コードとユーザーが指定したコールバックが、呼び出しが開始された元のセキュリティ コンテキストとは異なるセキュリティ コンテキストで実行される場合があります。次のようなコンテキストが含まれます。  
  
    -   アプリケーションのアクセス許可コンテキスト。  
  
    -   現在実行している <xref:System.AppDomain> の有効期間中に、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の呼び出しに使用される他のユーザー スレッドが以前に作成したスレッド固有のアクセス許可コンテキスト。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] パブリック API の呼び出しの前に、完全信頼コンポーネントによってこのようなアクセス許可がアサートされない限り、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、部分信頼コードで完全信頼アクセス許可を取得できないことが保証されます。ただし、完全信頼をアサートした効果が特定のスレッド、操作、またはユーザー操作として隔離されることは保証されません。  
  
 <xref:System.Security.PermissionSet.Assert%2A>、<xref:System.Security.PermissionSet.PermitOnly%2A>、または <xref:System.Security.PermissionSet.Deny%2A> を呼び出すことにより、スレッド固有のアクセス許可コンテキストを作成しないことをお勧めします。代わりに、<xref:System.Security.PermissionSet.Assert%2A>、<xref:System.Security.PermissionSet.Deny%2A>、または <xref:System.Security.PermissionSet.PermitOnly%2A> が不要となるように、アプリケーション自体に特権を付与するか、特権を拒否します。  
  
## 参照  
 <xref:System.Runtime.Serialization.DataContractSerializer>   
 <xref:System.Xml.Serialization.IXmlSerializable>