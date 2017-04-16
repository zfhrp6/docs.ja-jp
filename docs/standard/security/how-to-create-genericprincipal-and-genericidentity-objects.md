---
title: "方法 : GenericPrincipal オブジェクトと GenericIdentity オブジェクトを作成する | Microsoft Docs"
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
  - "作成 (GenericIdentity オブジェクトを)"
  - "作成 (GenericPrincipal オブジェクトを)"
  - "GenericIdentity オブジェクト"
  - "GenericPrincipal オブジェクト"
ms.assetid: 465694cf-258b-4747-9dae-35b01a5bcdbb
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : GenericPrincipal オブジェクトと GenericIdentity オブジェクトを作成する
<xref:System.Security.Principal.GenericIdentity> クラスを <xref:System.Security.Principal.GenericPrincipal> クラスと組み合わせて使用することによって、Windows NT ドメインや Windows 2000 ドメインから独立して存在する承認スキームを作成できます。  
  
### GenericPrincipal オブジェクトを作成するには  
  
1.  ID クラスの新しいインスタンスを作成し、インスタンスに付ける名前で初期化します。  新しい **GenericIdentity** オブジェクトを作成し、名前 `MyUser` で初期化するコードを次に示します。  
  
    ```vb  
    Dim MyIdentity As New GenericIdentity("MyUser")  
    ```  
  
    ```csharp  
    GenericIdentity MyIdentity = new GenericIdentity("MyUser");  
    ```  
  
2.  **GenericPrincipal** クラスの新しいインスタンスを作成し、前に作成した **GenericIdentity** オブジェクトと、プリンシパルに関連付けるロールを表す文字列の配列で、このインスタンスを初期化します。  管理者のロールとユーザーのロールを表す文字列の配列を指定するコード例を次に示します。  **GenericPrincipal** は、前の **GenericIdentity** と文字列配列で初期化されます。  
  
    ```vb  
    Dim MyStringArray As String() = {"Manager", "Teller"}  
    DIm MyPrincipal As New GenericPrincipal(MyIdentity, MyStringArray)  
    ```  
  
    ```csharp  
    String[] MyStringArray = {"Manager", "Teller"};  
    GenericPrincipal MyPrincipal = new GenericPrincipal(MyIdentity, MyStringArray);  
    ```  
  
3.  次のコードを使用して、プリンシパルを現在のスレッドに結合します。  この方法は、プリンシパルが 2 回以上検証される必要がある場合、アプリケーション内で実行されている他のコードによって検証される必要がある場合、または <xref:System.Security.Permissions.PrincipalPermission> オブジェクトによって検証される必要がある場合に便利です。  このような場合でも、プリンシパル オブジェクトをスレッドに結合せずにロール ベースの検証を行うことができます。  詳細については、「[プリンシパル オブジェクトの置き換え](../../../docs/standard/security/replacing-a-principal-object.md)」を参照してください。  
  
    ```vb  
    Thread.CurrentPrincipal = MyPrincipal  
    ```  
  
    ```csharp  
    Thread.CurrentPrincipal = MyPrincipal;  
    ```  
  
## 使用例  
 **GenericPrincipal** と **GenericIdentity** のインスタンスを作成する方法を示すコードを次に示します。  このコードは、各オブジェクトの値をコンソールに表示します。  
  
```vb  
Imports System  
Imports System.Security.Principal  
Imports System.Threading  
  
Public Class Class1  
  
    Public Shared Sub Main()  
        ' Create generic identity.  
        Dim MyIdentity As New GenericIdentity("MyIdentity")  
  
        ' Create generic principal.  
        Dim MyStringArray As String() =  {"Manager", "Teller"}  
        Dim MyPrincipal As New GenericPrincipal(MyIdentity, MyStringArray)  
  
        ' Attach the principal to the current thread.  
        ' This is not required unless repeated validation must occur,  
        ' other code in your application must validate, or the   
        ' PrincipalPermisson object is used.   
        Thread.CurrentPrincipal = MyPrincipal  
  
        ' Print values to the console.  
        Dim Name As String = MyPrincipal.Identity.Name  
        Dim Auth As Boolean = MyPrincipal.Identity.IsAuthenticated  
        Dim IsInRole As Boolean = MyPrincipal.IsInRole("Manager")  
  
        Console.WriteLine("The Name is: {0}", Name)  
        Console.WriteLine("The IsAuthenticated is: {0}", Auth)  
        Console.WriteLine("Is this a Manager? {0}", IsInRole)  
  
    End Sub  
  
End Class  
```  
  
```csharp  
using System;  
using System.Security.Principal;  
using System.Threading;  
  
public class Class1  
{  
    public static int Main(string[] args)  
    {  
    // Create generic identity.  
    GenericIdentity MyIdentity = new GenericIdentity("MyIdentity");  
  
    // Create generic principal.  
    String[] MyStringArray = {"Manager", "Teller"};  
    GenericPrincipal MyPrincipal =   
        new GenericPrincipal(MyIdentity, MyStringArray);  
  
    // Attach the principal to the current thread.  
    // This is not required unless repeated validation must occur,  
    // other code in your application must validate, or the   
    // PrincipalPermisson object is used.   
    Thread.CurrentPrincipal = MyPrincipal;  
  
    // Print values to the console.  
    String Name =  MyPrincipal.Identity.Name;  
    bool Auth =  MyPrincipal.Identity.IsAuthenticated;   
    bool IsInRole =  MyPrincipal.IsInRole("Manager");  
  
    Console.WriteLine("The Name is: {0}", Name);  
    Console.WriteLine("The IsAuthenticated is: {0}", Auth);  
    Console.WriteLine("Is this a Manager? {0}", IsInRole);  
  
    return 0;  
    }  
}  
```  
  
 実行されると、アプリケーションは次のような出力を表示します。  
  
```  
The Name is: MyIdentity  
The IsAuthenticated is: True  
Is this a Manager? True  
```  
  
## 参照  
 <xref:System.Security.Principal.GenericIdentity>   
 <xref:System.Security.Principal.GenericPrincipal>   
 <xref:System.Security.Permissions.PrincipalPermission>   
 [プリンシパル オブジェクトの置き換え](../../../docs/standard/security/replacing-a-principal-object.md)   
 [プリンシパル オブジェクトと ID オブジェクト](../../../docs/standard/security/principal-and-identity-objects.md)