---
title: "方法 : WindowsPrincipal プロジェクトを作成する | Microsoft Docs"
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
  - "プリンシパル オブジェクト, 作成"
  - "セキュリティ [.NET Framework], 作成 (WindowsPrincipal オブジェクトを)"
  - "セキュリティ [.NET Framework], プリンシパル"
  - "WindowsPrincipal オブジェクト, 作成"
ms.assetid: 56eb10ca-e61d-4ed2-af7a-555fc4c25a25
caps.latest.revision: 14
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : WindowsPrincipal プロジェクトを作成する
コードが役割ベースの検証を繰り返し実行する必要があるか、1 回だけ実行する必要があるかによって、<xref:System.Security.Principal.WindowsPrincipal> オブジェクトを作成する方法は 2 つあります。  
  
 コードが役割ベースの検証を繰り返し実行する必要がある場合、次の最初の手順のほうが、生成されるオーバーヘッドが少なくなります。  コードが役割ベースの検証を 1 回だけ実行する必要がある場合、次の 2 番目の手順を使用して <xref:System.Security.Principal.WindowsPrincipal> オブジェクトを作成できます。  
  
### 繰り返し検証で WindowsPrincipal オブジェクトを作成するには  
  
1.  静的な <xref:System.AppDomain.CurrentDomain%2A?displayProperty=fullName> プロパティによって返される <xref:System.AppDomain> オブジェクトの <xref:System.AppDomain.SetPrincipalPolicy%2A> メソッドを呼び出し、新しいポリシーの内容を示す <xref:System.Security.Principal.PrincipalPolicy> 列挙値があるメソッドに渡します。  サポートされる値は <xref:System.Security.Principal.PrincipalPolicy>、<xref:System.Security.Principal.PrincipalPolicy>、および <xref:System.Security.Principal.PrincipalPolicy> です。  次のコードは、このメソッドの呼び出しを示しています。  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2.  ポリシーの設定により、静的な <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=fullName> プロパティを使用して、現在の Windows ユーザーをカプセル化するプリンシパルを取得します。  プロパティの戻り値の型は <xref:System.Security.Principal.IPrincipal> であるため、結果を <xref:System.Security.Principal.WindowsPrincipal> 型にキャストする必要があります。  次のコードは、新しい <xref:System.Security.Principal.WindowsPrincipal> オブジェクトを、現在のスレッドに関連付けられたプリンシパルの値に初期化します。  
  
    ```csharp  
    WindowsPrincipal MyPrincipal =   
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim MyPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)   
    ```  
  
3.  プリンシパル オブジェクトが作成されると、いくつかのメソッドのいずれかを使用して検証できます。  
  
### 1 回の検証用に WindowsPrincipal オブジェクトを作成するには  
  
1.  静的な <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=fullName> メソッドを呼び出して新しい <xref:System.Security.Principal.WindowsIdentity> オブジェクトを初期化します。このメソッドは、現在の Windows アカウントに対してクエリを実行し、そのアカウントに関する情報を新規作成された ID オブジェクトに配置します。  次のコードは、<xref:System.Security.Principal.WindowsIdentity> オブジェクトを新規作成し、これを現在の認証済みユーザーに初期化します。  
  
    ```csharp  
    WindowsIdentity MyIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim MyIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2.  <xref:System.Security.Principal.WindowsPrincipal> オブジェクトを新規作成し、これに前の手順で作成された <xref:System.Security.Principal.WindowsIdentity> オブジェクトの値を渡します。  
  
    ```csharp  
    WindowsPrincipal MyPrincipal = new WindowsPrincipal(MyIdentity);  
    ```  
  
    ```vb  
    Dim MyPrincipal As New WindowsPrincipal(MyIdentity)  
    ```  
  
3.  プリンシパル オブジェクトが作成されると、いくつかのメソッドのいずれかを使用して検証できます。  
  
## 参照  
 [プリンシパル オブジェクトと ID オブジェクト](../../../docs/standard/security/principal-and-identity-objects.md)