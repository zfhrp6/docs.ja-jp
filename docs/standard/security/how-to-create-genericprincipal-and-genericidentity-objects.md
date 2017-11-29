---
title: "方法 : GenericPrincipal オブジェクトと GenericIdentity オブジェクトを作成する"
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
- Creating Generic Identity Objects
- GenericPrincipal Objects
- Creating GenericPrincipal Objects
- GenericIdentity Objects
ms.assetid: 465694cf-258b-4747-9dae-35b01a5bcdbb
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 93cd88d0321133a8340864645954b450a8e530ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-genericprincipal-and-genericidentity-objects"></a><span data-ttu-id="25869-102">方法 : GenericPrincipal オブジェクトと GenericIdentity オブジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="25869-102">How to: Create GenericPrincipal and GenericIdentity Objects</span></span>
<span data-ttu-id="25869-103">使用することができます、<xref:System.Security.Principal.GenericIdentity>クラスと組み合わせて、 <xref:System.Security.Principal.GenericPrincipal> Windows ドメインの独立に存在する認証スキームを作成するクラス。</span><span class="sxs-lookup"><span data-stu-id="25869-103">You can use the <xref:System.Security.Principal.GenericIdentity> class in conjunction with the <xref:System.Security.Principal.GenericPrincipal> class to create an authorization scheme that exists independent of a Windows domain.</span></span>  
  
### <a name="to-create-a-genericprincipal-object"></a><span data-ttu-id="25869-104">GenericPrincipal オブジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="25869-104">To create a GenericPrincipal object</span></span>  
  
1.  <span data-ttu-id="25869-105">ID クラスの新しいインスタンスを作成し、インスタンスに付ける名前で初期化します。</span><span class="sxs-lookup"><span data-stu-id="25869-105">Create a new instance of the identity class and initialize it with the name you want it to hold.</span></span> <span data-ttu-id="25869-106">新しい **GenericIdentity** オブジェクトを作成し、名前 `MyUser` で初期化するコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="25869-106">The following code creates a new **GenericIdentity** object and initializes it with the name `MyUser`.</span></span>  
  
    ```vb  
    Dim MyIdentity As New GenericIdentity("MyUser")  
    ```  
  
    ```csharp  
    GenericIdentity MyIdentity = new GenericIdentity("MyUser");  
    ```  
  
2.  <span data-ttu-id="25869-107">**GenericPrincipal** クラスの新しいインスタンスを作成し、前に作成した **GenericIdentity** オブジェクトと、プリンシパルに関連付けるロールを表す文字列の配列で、このインスタンスを初期化します。</span><span class="sxs-lookup"><span data-stu-id="25869-107">Create a new instance of the **GenericPrincipal** class and initialize it with the previously created **GenericIdentity** object and an array of strings that represent the roles that you want associated with this principal.</span></span> <span data-ttu-id="25869-108">管理者のロールとユーザーのロールを表す文字列の配列を指定するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="25869-108">The following code example specifies an array of strings that represent an administrator role and a user role.</span></span> <span data-ttu-id="25869-109">**GenericPrincipal** は、前の **GenericIdentity** と文字列配列で初期化されます。</span><span class="sxs-lookup"><span data-stu-id="25869-109">The **GenericPrincipal** is then initialized with the previous **GenericIdentity** and the string array.</span></span>  
  
    ```vb  
    Dim MyStringArray As String() = {"Manager", "Teller"}  
    DIm MyPrincipal As New GenericPrincipal(MyIdentity, MyStringArray)  
    ```  
  
    ```csharp  
    String[] MyStringArray = {"Manager", "Teller"};  
    GenericPrincipal MyPrincipal = new GenericPrincipal(MyIdentity, MyStringArray);  
    ```  
  
3.  <span data-ttu-id="25869-110">次のコードを使用して、プリンシパルを現在のスレッドに結合します。</span><span class="sxs-lookup"><span data-stu-id="25869-110">Use the following code to attach the principal to the current thread.</span></span> <span data-ttu-id="25869-111">これは、プリンシパルが何回かを検証する必要があります、アプリケーションで実行されているその他のコードを検証する必要がありますまたはで検証する必要がある場合、<xref:System.Security.Permissions.PrincipalPermission>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="25869-111">This is valuable in situations where the principal must be validated several times, it must be validated by other code running in your application, or it must be validated by a <xref:System.Security.Permissions.PrincipalPermission> object.</span></span> <span data-ttu-id="25869-112">このような場合でも、プリンシパル オブジェクトをスレッドに結合せずにロール ベースの検証を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="25869-112">You can still perform role-based validation on the principal object without attaching it to the thread.</span></span> <span data-ttu-id="25869-113">詳細については、「[プリンシパル オブジェクトの置き換え](../../../docs/standard/security/replacing-a-principal-object.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="25869-113">For more information, see [Replacing a Principal Object](../../../docs/standard/security/replacing-a-principal-object.md).</span></span>  
  
    ```vb  
    Thread.CurrentPrincipal = MyPrincipal  
    ```  
  
    ```csharp  
    Thread.CurrentPrincipal = MyPrincipal;  
    ```  
  
## <a name="example"></a><span data-ttu-id="25869-114">例</span><span class="sxs-lookup"><span data-stu-id="25869-114">Example</span></span>  
 <span data-ttu-id="25869-115">次のコード例では、**GenericPrincipal** と **GenericIdentity** のインスタンスを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="25869-115">The following code example demonstrates how to create an instance of a **GenericPrincipal** and a **GenericIdentity**.</span></span> <span data-ttu-id="25869-116">このコードは、各オブジェクトの値をコンソールに表示します。</span><span class="sxs-lookup"><span data-stu-id="25869-116">This code displays the values of these objects to the console.</span></span>  
  
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
  
 <span data-ttu-id="25869-117">実行されると、アプリケーションの出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="25869-117">When executed, the application displays output similar to the following.</span></span>  
  
```  
The Name is: MyIdentity  
The IsAuthenticated is: True  
Is this a Manager? True  
```  
  
## <a name="see-also"></a><span data-ttu-id="25869-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="25869-118">See Also</span></span>  
 <xref:System.Security.Principal.GenericIdentity>  
 <xref:System.Security.Principal.GenericPrincipal>  
 <xref:System.Security.Permissions.PrincipalPermission>  
 [<span data-ttu-id="25869-119">プリンシパル オブジェクトの置き換え</span><span class="sxs-lookup"><span data-stu-id="25869-119">Replacing a Principal Object</span></span>](../../../docs/standard/security/replacing-a-principal-object.md)  
 [<span data-ttu-id="25869-120">プリンシパル オブジェクトと ID オブジェクト</span><span class="sxs-lookup"><span data-stu-id="25869-120">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
