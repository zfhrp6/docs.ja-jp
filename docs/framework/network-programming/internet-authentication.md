---
title: "インターネット認証 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "認証 [.NET Framework]、クラス"
  - "IAuthenticationModule インターフェイス"
  - "ICredentialLookup インターフェイス"
  - "CredentialCache クラス、CredentialCache クラスについて"
  - "受信 (データの)、認証"
  - "AuthenticationManager クラス、AuthenticationManager クラスについて"
  - "インターネット、認証"
  - "送信 (データの)、認証"
  - "ネットワーク リソース、認証"
  - "ユーザー認証、認証用のクラス"
  - "NetworkCredential クラス、NetworkCredential クラスについて"
  - "クライアント認証、認証用のクラス"
ms.assetid: d342e87c-f672-4660-a513-41a2f2b80c4a
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# インターネット認証
<xref:System.Net> クラス、ダイジェスト基本支えましたり、標準的なインターネット認証方法など、さまざまなクライアント認証方法が、NTLM 認証および Kerberos、作成できるカスタム メソッド交渉します。  
  
 認証の資格情報は、<xref:System.Net.ICredentials> のインターフェイスを実装する <xref:System.Net.NetworkCredential> と <xref:System.Net.CredentialCache> クラスに保存されます。  これらのクラスの 1 種類が資格ついてはただされると、**NetworkCredential** クラスのインスタンスを返します。  認証プロセスは <xref:System.Net.AuthenticationManager> クラスによって管理され、実際の認証プロセスは <xref:System.Net.IAuthenticationModule> のインターフェイスを実装する認証のモジュール クラスによって行われます。  使用する前に **AuthenticationManager** の注文の認証のモジュールを登録する必要があります; 基本のモジュール、ダイジェスト、NTLM 交渉 Kerberos 認証および認証方法は既定で登録されます。  
  
 **NetworkCredential** は URI によって識別される一つのインターネットのリソースに関連付けられている一連の資格情報を保存したり、必要に応じて <xref:System.Net.NetworkCredential.GetCredential%2A> 方法にそれらを返します。  **NetworkCredential** クラスは、インターネットでのリソースまたは資格情報のセットを同じどちらの場合も使用するアプリケーションによる制限数をアプリケーション アクセスして通常使用されます。  
  
 **\[CredentialCache\]** クラスは、さまざまな Web のリソースの資格情報の収集を格納します。  <xref:System.Net.CredentialCache.GetCredential%2A> 方法が呼び出されたときに、**\[CredentialCache\]** は Web リソースおよび要求された認証スキームの URI によって決定されるように適切な資格情報のセットを、返します。  **\[CredentialCache\]** クラスを使用した異なる認証スキームのさまざまなインターネットのリソースを対象に使用するアプリケーションは、必要に応じてすべての資格情報を保存するため、それらを提供します。  
  
 インターネットのリソースが認証が必要な場合、<xref:System.Net.WebRequest.GetResponse%2A?displayProperty=fullName> 方法は、資格情報の要求とともに **AuthenticationManager** に <xref:System.Net.WebRequest> を送信します。  要求は次のプロセスに従って、認証します:  
  
1.  **AuthenticationManager** は、が登録された順序で登録認証のモジュールそれぞれに <xref:System.Net.IAuthenticationModule.Authenticate%2A> 方法を追加します。  **AuthenticationManager** は、認証プロセスを実行するに **null** を戻さない最初のモジュールを使用します。  プロセスの詳細が含まれる認証のモジュールのタイプによって異なります。  
  
2.  認証プロセスが完了すると、インターネット リソースのアクセスを必要な情報を含む認証のモジュールの **\[WebRequest\]** に <xref:System.Net.Authorization> を返します。  
  
 ある認証スキームは、リソースのユーザーを認証要求できます。  したがって、アプリケーションは、リソースがより高いユーザーを preauthenticating すると時間を節約できます。サーバーに 1 回以上ラウンド トリップを削除します。  または、プログラムの起動時にユーザーによって関連で認証を後で実行できます。  preauthentication を使用して認証スキームは **true**に [&#91;CanPreAuthenticate&#93;](frlrfsystemnetiauthenticationmoduleclasspreauthenticatetopic) のプロパティを設定します。  
  
## 参照  
 [基本認証とダイジェスト認証](../../../docs/framework/network-programming/basic-and-digest-authentication.md)   
 [NTLM 認証および Kerberos 認証](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)   
 [ネットワーク プログラミングにおけるセキュリティ](../../../docs/framework/network-programming/security-in-network-programming.md)