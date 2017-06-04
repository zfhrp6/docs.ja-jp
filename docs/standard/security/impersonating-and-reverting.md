---
title: "偽装と復帰 | Microsoft Docs"
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
  - "偽装 (Windows アカウントを)"
  - "セキュリティ [.NET Framework], 偽装 (Windows アカウントを)"
  - "WindowsIdentity オブジェクト, 偽装"
ms.assetid: b93d402c-6c28-4f50-b2bc-d9607dc3e470
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 11
---
# 偽装と復帰
場合によっては、Windows NT アカウント トークンを取得して、Windows アカウントを偽装する必要があります。 たとえば、ASP.NET ベースのアプリケーションが、時間によって複数のユーザーの代わりに操作しなければならない場合があります。 その場合、アプリケーションはインターネット インフォメーション サービス \(IIS\) から管理者を表すトークンを受け入れて、そのユーザーを偽装し、操作を実行してから前の ID に戻ります。 続いて、IIS から管理者より権限が少ないユーザーを表すトークンを受け入れ、操作を実行してから、また元に戻ります。  
  
 アプリケーションが、IIS によって現在のスレッドにアタッチされていない Windows アカウントを偽装しなければならない場合は、そのアカウントのトークンを取得し、そのトークンを使用してアカウントをアクティブ化する必要があります。 それには、次のタスクを実行します。  
  
1.  アンマネージ **LogonUser** メソッドを呼び出すことによって、特定のユーザーのアカウント トークンを取得します。 このメソッドは、.NET Framework の基底クラス ライブラリには含まれていませんが、アンマネージ **advapi32.dll** 内にあります。 アンマネージ コード内のメソッドへのアクセスは高度な操作であり、ここでは説明しません。 詳細については、「[アンマネージ コードとの相互運用](../../../docs/framework/interop/index.md)」を参照してください。**LogonUser** メソッドと **advapi32.dll** の詳細については、プラットフォーム SDK ドキュメントを参照してください。  
  
2.  **WindowsIdentity** クラスの新しいインスタンスを作成し、トークンを渡します。 次のコードに、この呼び出しを示します。ここで、`hToken` は Windows トークンを表します。  
  
    ```csharp  
    WindowsIdentity ImpersonatedIdentity = new WindowsIdentity(hToken);  
  
    ```  
  
    ```vb  
    Dim ImpersonatedIdentity As New WindowsIdentity(hToken)  
    ```  
  
3.  このコードに示されているように、<xref:System.Security.Principal.WindowsImpersonationContext> クラスの新しいインスタンスを作成し、そのインスタンスを、初期化されたクラスの <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=fullName> メソッドで初期化することで、偽装を開始します。  
  
    ```csharp  
    WindowsImpersonationContext MyImpersonation = ImpersonatedIdentity.Impersonate();  
  
    ```  
  
    ```vb  
    WindowsImpersonationContext MyImpersonation = ImpersonatedIdentity.Impersonate()  
    ```  
  
4.  偽装する必要がなくなったら、以下のコードに示されているように <xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=fullName> メソッドを呼び出して、偽装を元に戻します。  
  
    ```csharp  
    MyImpersonation.Undo();  
  
    ```  
  
    ```vb  
    MyImpersonation.Undo()  
    ```  
  
 信頼されるコードが既に <xref:System.Security.Principal.WindowsPrincipal> オブジェクトをスレッドにアタッチしている場合は、アカウント トークンを取らないインスタンス メソッド **Impersonate** を呼び出すことができます。 この方法が役立つのは、スレッドで **WindowsPrincipal** オブジェクトが表しているユーザーが、現在プロセスが実行されているユーザーではない場合のみです。 このような状態は、たとえば、Windows 認証を有効にして、偽装を無効にした ASP.NET を使用している場合に発生することがあります。 その場合、プロセスはインターネット インフォメーション サービス \(IIS\) で構成されたアカウントで実行されますが、現在のプリンシパルは、ページにアクセスしている Windows ユーザーを表しています。  
  
 **Impersonate** と **Undo** のいずれも、現在の呼び出しコンテキストに関連する **Principal** オブジェクト \(<xref:System.Security.Principal.IPrincipal>\) を変更しないことに注意してください。 偽装と元に戻す操作によって変更されるのは、現在のオペレーティング システム プロセスに関連付けたトークンです。  
  
## 参照  
 <xref:System.Security.Principal.WindowsIdentity>   
 <xref:System.Security.Principal.WindowsImpersonationContext>   
 [プリンシパル オブジェクトと ID オブジェクト](../../../docs/standard/security/principal-and-identity-objects.md)   
 [アンマネージ コードとの相互運用](../../../docs/framework/interop/index.md)