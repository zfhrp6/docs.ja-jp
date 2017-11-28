---
title: "プリンシパル オブジェクトと ID オブジェクト"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WindowsIdentity objects
- GenericIdentity objects
- GenericPrincipal objects
- identity objects, about identity objects
- security [.NET Framework], identity objects
- principal objects, about principal objects
- security [.NET Framework], principals
- WindowsPrincipal objects
ms.assetid: aa5930ad-f3d7-40aa-b6f6-c6edcd5c64f7
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ce3c5ce3d79a36320eee6b7312518d2559509127
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="principal-and-identity-objects"></a>プリンシパル オブジェクトと ID オブジェクト
マネージ コードには、id またはを通じてプリンシパルの役割を検出できる、<xref:System.Security.Principal.IPrincipal>への参照を含むオブジェクトを<xref:System.Security.Principal.IIdentity>オブジェクト。 ID オブジェクトとプリンシパル オブジェクトは、ユーザーとグループ アカウントのようななじみのある概念と比較するとわかりやすいでしょう。 ほとんどのネットワーク環境で、ユーザー アカウントは人またはプログラムを表し、グループ アカウントは特定のカテゴリのユーザーやそのユーザーが所有する権限を表します。 同様に、.NET Framework の ID オブジェクトはユーザーを表し、ロールはメンバーシップやセキュリティ コンテキストを表します。 .NET Framework で、プリンシパル オブジェクトは、ID オブジェクトとロールの両方をカプセル化します。 .NET Framework アプリケーションは、ID または一般的にはロール メンバーシップに基づいてプリンシパルに権限を付与します。  
  
## <a name="identity-objects"></a>ID オブジェクト  
 ID オブジェクトは、検証対象のユーザーまたはエンティティに関する情報をカプセル化します。 ID オブジェクトの最も基本的なレベルには名前と認証の種類が含まれます。 名前はユーザー名または Windows アカウント名、認証の種類は、サポートされるログオン プロトコル (Kerberos V5 など) かカスタム値になります。 .NET Framework を定義、<xref:System.Security.Principal.GenericIdentity>のほとんどのカスタム ログオン シナリオや、特殊化されて使用できるオブジェクト<xref:System.Security.Principal.WindowsIdentity>Windows 認証に依存するアプリケーションで、使用するときに使用できるオブジェクト。 また、カスタム ユーザー情報をカプセル化する独自の ID クラスを定義することもできます。  
  
 <xref:System.Security.Principal.IIdentity>インターフェイスは、名前と Kerberos V5 または NTLM など、認証の種類にアクセスするためのプロパティを定義します。 すべての **Identity** クラスでは **IIdentity** インターフェイスが実装されます。 **ID** オブジェクトと、スレッドが現在実行している Windows NT プロセス トークンの間に関係は必要ありません。 ただし、**ID** オブジェクトが **WindowsIdentity** オブジェクトである場合、ID は Windows NT セキュリティ トークンを表すと見なされます。  
  
## <a name="principal-objects"></a>プリンシパル オブジェクト  
 プリンシパル オブジェクトは、コードが実行されているセキュリティ コンテキストを表します。 ロールベースのセキュリティを実装するアプリケーションは、プリンシパル オブジェクトに関連付けられたロールに基づいて権限を付与します。 Id オブジェクトと同様に、.NET Framework には、<xref:System.Security.Principal.GenericPrincipal>オブジェクトおよび<xref:System.Security.Principal.WindowsPrincipal>オブジェクト。 独自のカスタム プリンシパル クラスを定義することもできます。  
  
 <xref:System.Security.Principal.IPrincipal>インターフェイスへのアクセスに関連するプロパティを定義する**Identity**オブジェクトで、ユーザーが識別されるかどうかを決定するためのメソッドだけでなく、**プリンシパル**オブジェクトのメンバーである、指定されたロールです。 すべての**プリンシパル** クラスは、**IPrincipal** インターフェイスの他に、必要なその他のプロパティとメソッドを実装しています。 たとえば、共通言語ランタイムでは **WindowsPrincipal** クラスが提供されますが、これは Windows NT または Windows 2000 グループ メンバーシップをロールにマッピングする追加機能を実装します。  
  
 A**プリンシパル**オブジェクトが呼び出しコンテキストにバインド (<xref:System.Runtime.Remoting.Messaging.CallContext>) アプリケーション ドメイン内のオブジェクト (<xref:System.AppDomain>)。 常に既定の呼び出しコンテキストはそれぞれ新しい **AppDomain** を使用して作成されるため、**プリンシパル** オブジェクトを受け入れる呼び出しコンテキストが常に存在します。 新しいスレッドが作成されるとき、そのスレッドの **CallContext** オブジェクトも作成されます。 **プリンシパル** オブジェクトの参照は、作成スレッドから新しいスレッドの **CallContext** に自動的にコピーされます。 スレッドの作成者に所属する**プリンシパル** オブジェクトをランタイムが判別できない場合は、**プリンシパル** オブジェクトと **ID** オブジェクトの作成で既定のポリシーに従います。  
  
 構成可能なアプリケーション ドメイン固有のポリシーによって、新しいアプリケーション ドメインに関連付ける**プリンシパル** オブジェクトの種類を決める規則が定義されます。 セキュリティ ポリシーによって許可される場合、ランタイムは、現在の実行スレッドに関連するオペレーティング システム トークンを反映する**プリンシパル** オブジェクトと **ID** オブジェクトを作成できます。 ランタイムは既定では、認証されていないユーザーを表す**プリンシパル** オブジェクトと **ID** オブジェクトを使用します。 このような既定の**プリンシパル** オブジェクトと **ID** オブジェクトは、コードがアクセスを試行するまでランタイムによって作成されることはありません。  
  
 信頼されるコードが、アプリケーション ドメインを作成して、アプリケーション ドメイン ポリシーを作成できます。このポリシーによって、既定の**プリンシパル** オブジェクトと **ID** オブジェクトのコンストラクトが制御されます。 このアプリケーション ドメイン固有ポリシーは、そのアプリケーション ドメインのすべての実行スレッドに適用されます。 管理されていない、信頼されたホストは本質的に、このポリシーを設定する権限を持ちますが、このポリシー設定を管理対象のコードが必要、<xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>ドメイン ポリシーを制御するためです。  
  
 **プリンシパル** オブジェクトを同じプロセス内 (つまり同じコンピューター上の) アプリケーション ドメイン間で送信するとき、リモート処理インフラストラクチャが、呼び出し元のコンテキストに関連する**プリンシパル** オブジェクトへの参照を呼び出し先のコンテキストにコピーします。  
  
## <a name="see-also"></a>関連項目  
 [方法: WindowsPrincipal オブジェクトを作成する](../../../docs/standard/security/how-to-create-a-windowsprincipal-object.md)  
 [方法: GenericPrincipal オブジェクトと GenericIdentity オブジェクトを作成する](../../../docs/standard/security/how-to-create-genericprincipal-and-genericidentity-objects.md)  
 [プリンシパル オブジェクトの置き換え](../../../docs/standard/security/replacing-a-principal-object.md)  
 [偽装と復帰](../../../docs/standard/security/impersonating-and-reverting.md)  
 [ロール ベースのセキュリティ](../../../docs/standard/security/role-based-security.md)  
 [セキュリティの基本概念](../../../docs/standard/security/key-security-concepts.md)
