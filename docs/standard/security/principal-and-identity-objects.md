---
title: "プリンシパル オブジェクトと ID オブジェクト | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "GenericIdentity オブジェクト"
  - "GenericPrincipal オブジェクト"
  - "ID オブジェクト, ID オブジェクトの概要"
  - "プリンシパル オブジェクト, プリンシパル オブジェクトの概要"
  - "セキュリティ [.NET Framework], ID オブジェクト"
  - "セキュリティ [.NET Framework], プリンシパル"
  - "WindowsIdentity オブジェクト"
  - "WindowsPrincipal オブジェクト"
ms.assetid: aa5930ad-f3d7-40aa-b6f6-c6edcd5c64f7
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# プリンシパル オブジェクトと ID オブジェクト
マネージ コードは、[Identity](frlrfSystemSecurityPrincipalIIdentityClassTopic) オブジェクトへの参照が含まれる [Principal](frlrfSystemSecurityPrincipalIPrincipalClassTopic) オブジェクトを通じて、プリンシパルの ID またはロールを検出できます。  ID オブジェクトとプリンシパル オブジェクトは、ユーザー アカウントとグループ アカウントなど、よく知られた概念にたとえることができます。  ほとんどのネットワーク環境では、ユーザー アカウントは人またはプログラムを表し、グループ アカウントはユーザーの特定のカテゴリとユーザーの所有する権限を表します。  これと同様に、.NET Framework の ID オブジェクトはユーザーを表し、ロールはメンバーシップとセキュリティ コンテキストを表します。  .NET Framework のプリンシパル オブジェクトは、ID オブジェクトとロールの両方をカプセル化します。.NET Framework アプリケーションは、ID に基づいて、またはより一般的にはロール メンバーシップに基づいて、プリンシパルに権限を与えます。  
  
## ID オブジェクト  
 ID オブジェクトは、検証するユーザーまたはエンティティについての情報をカプセル化します。  ID オブジェクトには、その最も基本的なレベルに名前と認証の種類が含まれます。  名前は、ユーザー名または Windows アカウント名です。認証の種類は、サポートされるログオン プロトコル \(Kerberos V5 など\) またはカスタム値です。  .NET Framework は、カスタムのログオン手順のほとんどで使用できる <xref:System.Security.Principal.GenericIdentity> オブジェクトと、アプリケーションで Windows 認証を利用するときに使用できる、より特化した <xref:System.Security.Principal.WindowsIdentity> オブジェクトを定義します。  また、カスタム ユーザー情報をカプセル化する独自の ID クラスを定義できます。  
  
 <xref:System.Security.Principal.IIdentity> インターフェイスは、名前と認証の種類 \(Kerberos V5 や NTLM など\) にアクセスするためのプロパティを定義します。  すべての **Identity** クラスは、**IIdentity** インターフェイスを実装します。  **Identity** オブジェクトと、スレッドが現在実行されている Windows NT プロセス トークンとの間に必要とされる関係はありません。  ただし、**Identity** オブジェクトが **WindowsIdentity** オブジェクトである場合は、ID が Windows NT セキュリティ トークンを表すものと想定されます。  
  
## プリンシパル オブジェクト  
 プリンシパル オブジェクトは、コードが実行されているセキュリティ コンテキストを表します。  ロール ベース セキュリティを実装するアプリケーションは、プリンシパル オブジェクトに関連付けられたロールに基づいて権限を与えます。  ID オブジェクトと同様に、.NET Framework には <xref:System.Security.Principal.GenericPrincipal> オブジェクトと <xref:System.Security.Principal.WindowsPrincipal> オブジェクトが用意されています。  独自のカスタム プリンシパル クラスを定義することもできます。  
  
 <xref:System.Security.Principal.IPrincipal> インターフェイスは、関連付けられた **Identity** オブジェクトにアクセスするためのプロパティと、**Principal** オブジェクトによって識別されるユーザーが特定のロールのメンバーかどうかを調べるためのメソッドを定義します。  すべての **Principal** クラスは、**IPrincipal** インターフェイス、およびその他の必要なプロパティとメソッドを実装します。  たとえば、共通言語ランタイムには **WindowsPrincipal** クラスが用意されています。このクラスは、Windows NT グループ メンバーシップまたは Windows 2000 グループ メンバーシップをロールに割り当てるための追加機能を実装します。  
  
 **Principal** オブジェクトは、アプリケーション ドメイン \(<xref:System.AppDomain>\) 内の呼び出しコンテキスト \(<xref:System.Runtime.Remoting.Messaging.CallContext>\) オブジェクトにバインドされています。  新しい **AppDomain** ごとに既定の呼び出しコンテキストが作成されるため、**Principal** オブジェクトを承認するために使用できる呼び出しコンテキストが必ず存在します。  新しいスレッドが作成されると、そのスレッドに対して **CallContext** オブジェクトも作成されます。  **Principal** オブジェクトの参照は、作成元スレッドから新しいスレッドの **CallContext** に自動的にコピーされます。  スレッドの作成元に属す **Principal** オブジェクトを特定できない場合、ランタイムは **Principal** オブジェクトと **Identity** オブジェクトを作成するための既定のポリシーに従います。  
  
 アプリケーション ドメインに固有の設定可能なポリシーは、新しいアプリケーション ドメインに関連付ける **Principal** オブジェクトの種類を決定するための規則を定義します。  セキュリティ ポリシーによって許可される場合、ランタイムは、現在の実行スレッドに関連付けられたオペレーティング システム トークンを反映する **Principal** オブジェクトと **Identity** オブジェクトを作成できます。  ランタイムは、既定では、認証されていないユーザーを表す **Principal** オブジェクトと **Identity** オブジェクトを使用します。  ランタイムは、既定の **Principal** オブジェクトと **Identity** オブジェクトを、これらのオブジェクトにコードがアクセスを試みるまで作成しません。  
  
 アプリケーション ドメインを作成する信頼されるコードは、既定の **Principal** オブジェクトと **Identity** オブジェクトの構築を制御するアプリケーション ドメイン ポリシーを設定できます。  アプリケーション ドメイン固有のポリシーは、そのアプリケーション ドメイン内のすべての実行スレッドに適用されます。  アンマネージの信頼される側のホストには、本来このポリシーを設定する能力がありますが、このポリシーを設定するマネージ コードは、ドメイン ポリシーを制御するための <xref:System.Security.Permissions.SecurityPermission?displayProperty=fullName> を持っている必要があります。  
  
 同じプロセス内 \(つまり同じコンピューター上\) の他のアプリケーション ドメインに **Principal** オブジェクトを転送する場合、リモート処理インフラストラクチャは、呼び出し元のコンテキストに関連付けられた **Principal** オブジェクトへの参照を、呼び出される側のコンテキストにコピーします。  
  
## 参照  
 [方法 : WindowsPrincipal プロジェクトを作成する](../../../docs/standard/security/how-to-create-a-windowsprincipal-object.md)   
 [方法 : GenericPrincipal オブジェクトと GenericIdentity オブジェクトを作成する](../../../docs/standard/security/how-to-create-genericprincipal-and-genericidentity-objects.md)   
 [プリンシパル オブジェクトの置き換え](../../../docs/standard/security/replacing-a-principal-object.md)   
 [偽装と復帰](../../../docs/standard/security/impersonating-and-reverting.md)   
 [ロール ベース セキュリティ](../../../docs/standard/security/role-based-security.md)   
 [セキュリティの基本概念](../../../docs/standard/security/key-security-concepts.md)