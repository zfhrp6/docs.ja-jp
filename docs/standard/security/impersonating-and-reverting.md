---
title: "偽装と復帰"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsIdentity objects, impersonating
- security [.NET Framework], impersonating Windows accounts
- impersonating Windows accounts
ms.assetid: b93d402c-6c28-4f50-b2bc-d9607dc3e470
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4d1bd053cacc677ca66fc2e2a9e14620e1d3a8b2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="impersonating-and-reverting"></a>偽装と復帰
場合によっては、Windows アカウント トークンを取得して、Windows アカウントを偽装する必要があります。 たとえば、ASP.NET ベースのアプリケーションが、時間によって複数のユーザーの代わりに操作しなければならない場合があります。 その場合、アプリケーションはインターネット インフォメーション サービス (IIS) から管理者を表すトークンを受け入れて、そのユーザーを偽装し、操作を実行してから前の ID に戻ります。 続いて、IIS から管理者より権限が少ないユーザーを表すトークンを受け入れ、操作を実行してから、また元に戻ります。  
  
 アプリケーションが、IIS によって現在のスレッドにアタッチされていない Windows アカウントを偽装しなければならない場合は、そのアカウントのトークンを取得し、そのトークンを使用してアカウントをアクティブ化する必要があります。 それには、次のタスクを実行します。  
  
1.  アンマネージ **LogonUser** メソッドを呼び出すことによって、特定のユーザーのアカウント トークンを取得します。 このメソッドは、.NET Framework の基底クラス ライブラリには含まれていませんが、アンマネージ **advapi32.dll** 内にあります。 アンマネージ コード内のメソッドへのアクセスは高度な操作であり、ここでは説明しません。 詳細については、「[アンマネージ コードとの相互運用](../../../docs/framework/interop/index.md)」を参照してください。 **LogonUser** メソッドと **advapi32.dll** の詳細については、プラットフォーム SDK ドキュメントを参照してください。  
  
2.  **WindowsIdentity** クラスの新しいインスタンスを作成し、トークンを渡します。 次のコードに、この呼び出しを示します。ここで、`hToken` は Windows トークンを表します。  
  
    ```csharp  
    WindowsIdentity ImpersonatedIdentity = new WindowsIdentity(hToken);  
    ```  
  
    ```vb  
    Dim ImpersonatedIdentity As New WindowsIdentity(hToken)  
    ```  
  
3.  新しいインスタンスを作成することで、偽装を開始、<xref:System.Security.Principal.WindowsImpersonationContext>クラスとで、初期化、<xref:System.Security.Principal.WindowsIdentity.Impersonate%2A?displayProperty=nameWithType>次のコードに示すように、初期化されたクラスのメソッドです。  
  
    ```csharp  
    WindowsImpersonationContext MyImpersonation = ImpersonatedIdentity.Impersonate();  
    ```  
  
    ```vb  
    WindowsImpersonationContext MyImpersonation = ImpersonatedIdentity.Impersonate()  
    ```  
  
4.  権限を借用が不要になったときに呼び出す、<xref:System.Security.Principal.WindowsImpersonationContext.Undo%2A?displayProperty=nameWithType>メソッドを次のコードに示すように、偽装を元に戻します。  
  
    ```csharp  
    MyImpersonation.Undo();  
    ```  
  
    ```vb  
    MyImpersonation.Undo()  
    ```  
  
 コードが既にアタッチされている信頼されている場合、<xref:System.Security.Principal.WindowsPrincipal>のスレッドにオブジェクトのインスタンス メソッドを呼び出すことができます**Impersonate**、アカウント トークンを受け取らないです。 この方法が役立つのは、スレッドで **WindowsPrincipal** オブジェクトが表しているユーザーが、現在プロセスが実行されているユーザーではない場合のみです。 このような状態は、たとえば、Windows 認証を有効にして、偽装を無効にした ASP.NET を使用している場合に発生することがあります。 その場合、プロセスはインターネット インフォメーション サービス (IIS) で構成されたアカウントで実行されますが、現在のプリンシパルは、ページにアクセスしている Windows ユーザーを表しています。  
  
 なお**Impersonate**も**を元に戻す**変更、**プリンシパル**オブジェクト (<xref:System.Security.Principal.IPrincipal>) 現在の呼び出しコンテキストに関連付けられています。 偽装と元に戻す操作によって変更されるのは、現在のオペレーティング システム プロセスに関連付けたトークンです。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Security.Principal.WindowsIdentity>  
 <xref:System.Security.Principal.WindowsImpersonationContext>  
 [プリンシパル オブジェクトと ID オブジェクト](../../../docs/standard/security/principal-and-identity-objects.md)  
 [アンマネージ コードとの相互運用](../../../docs/framework/interop/index.md)
