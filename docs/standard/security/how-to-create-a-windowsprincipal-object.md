---
title: '方法 : WindowsPrincipal プロジェクトを作成する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WindowsPrincipal objects, creating
- security [.NET Framework], creating a WindowsPrincipal object
- security [.NET Framework], principals
- principal objects, creating
ms.assetid: 56eb10ca-e61d-4ed2-af7a-555fc4c25a25
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f77d86e2ade841b715fc4bea8350d4e043bcb91b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581792"
---
# <a name="how-to-create-a-windowsprincipal-object"></a><span data-ttu-id="722e1-102">方法 : WindowsPrincipal プロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="722e1-102">How to: Create a WindowsPrincipal Object</span></span>
<span data-ttu-id="722e1-103">コードが役割ベースの検証を繰り返し実行する必要があるか、1 回だけ実行する必要があるかによって、<xref:System.Security.Principal.WindowsPrincipal> オブジェクトを作成する方法は 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="722e1-103">There are two ways to create a <xref:System.Security.Principal.WindowsPrincipal> object, depending on whether code must repeatedly perform role-based validation or must perform it only once.</span></span>  
  
 <span data-ttu-id="722e1-104">コードが役割ベースの検証を繰り返し実行する必要がある場合、次の最初の手順のほうが、生成されるオーバーヘッドが少なくなります。</span><span class="sxs-lookup"><span data-stu-id="722e1-104">If code must repeatedly perform role-based validation, the first of the following procedures produces less overhead.</span></span> <span data-ttu-id="722e1-105">コードが役割ベースの検証を 1 回だけ実行する必要がある場合、次の 2 番目の手順を使用して <xref:System.Security.Principal.WindowsPrincipal> オブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="722e1-105">When code needs to make role-based validations only once, you can create a <xref:System.Security.Principal.WindowsPrincipal> object by using the second of the following procedures.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-repeated-validation"></a><span data-ttu-id="722e1-106">繰り返し検証で WindowsPrincipal オブジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="722e1-106">To create a WindowsPrincipal object for repeated validation</span></span>  
  
1.  <span data-ttu-id="722e1-107">静的な <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> プロパティによって返される <xref:System.AppDomain> オブジェクトの <xref:System.AppDomain.SetPrincipalPolicy%2A> メソッドを呼び出し、新しいポリシーの内容を示す <xref:System.Security.Principal.PrincipalPolicy> 列挙値があるメソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="722e1-107">Call the <xref:System.AppDomain.SetPrincipalPolicy%2A> method on the <xref:System.AppDomain> object that is returned by the static <xref:System.AppDomain.CurrentDomain%2A?displayProperty=nameWithType> property, passing the method a <xref:System.Security.Principal.PrincipalPolicy> enumeration value that indicates what the new policy should be.</span></span> <span data-ttu-id="722e1-108">サポートされる値は <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>、<xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>、および <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal> です。</span><span class="sxs-lookup"><span data-stu-id="722e1-108">Supported values are <xref:System.Security.Principal.PrincipalPolicy.NoPrincipal>, <xref:System.Security.Principal.PrincipalPolicy.UnauthenticatedPrincipal>, and <xref:System.Security.Principal.PrincipalPolicy.WindowsPrincipal>.</span></span> <span data-ttu-id="722e1-109">次のコードは、このメソッドの呼び出しを示しています。</span><span class="sxs-lookup"><span data-stu-id="722e1-109">The following code demonstrates this method call.</span></span>  
  
    ```csharp  
    AppDomain.CurrentDomain.SetPrincipalPolicy(  
        PrincipalPolicy.WindowsPrincipal);  
    ```  
  
    ```vb  
    AppDomain.CurrentDomain.SetPrincipalPolicy( _  
        PrincipalPolicy.WindowsPrincipal)  
    ```  
  
2.  <span data-ttu-id="722e1-110">ポリシーの設定により、静的な <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> プロパティを使用して、現在の Windows ユーザーをカプセル化するプリンシパルを取得します。</span><span class="sxs-lookup"><span data-stu-id="722e1-110">With the policy set, use the static <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> property to retrieve the principal that encapsulates the current Windows user.</span></span> <span data-ttu-id="722e1-111">プロパティの戻り値の型は <xref:System.Security.Principal.IPrincipal> であるため、結果を <xref:System.Security.Principal.WindowsPrincipal> 型にキャストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="722e1-111">Because the property return type is <xref:System.Security.Principal.IPrincipal>, you must cast the result to a <xref:System.Security.Principal.WindowsPrincipal> type.</span></span> <span data-ttu-id="722e1-112">次のコードは、新しい <xref:System.Security.Principal.WindowsPrincipal> オブジェクトを、現在のスレッドに関連付けられたプリンシパルの値に初期化します。</span><span class="sxs-lookup"><span data-stu-id="722e1-112">The following code initializes a new <xref:System.Security.Principal.WindowsPrincipal> object to the value of the principal associated with the current thread.</span></span>  
  
    ```csharp  
    WindowsPrincipal MyPrincipal =   
        (WindowsPrincipal) Thread.CurrentPrincipal;  
    ```  
  
    ```vb  
    Dim MyPrincipal As WindowsPrincipal = _  
        CType(Thread.CurrentPrincipal, WindowsPrincipal)   
    ```  
  
3.  <span data-ttu-id="722e1-113">プリンシパル オブジェクトが作成されると、いくつかのメソッドのいずれかを使用して検証できます。</span><span class="sxs-lookup"><span data-stu-id="722e1-113">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
### <a name="to-create-a-windowsprincipal-object-for-a-single-validation"></a><span data-ttu-id="722e1-114">1 回の検証用に WindowsPrincipal オブジェクトを作成するには</span><span class="sxs-lookup"><span data-stu-id="722e1-114">To create a WindowsPrincipal object for a single validation</span></span>  
  
1.  <span data-ttu-id="722e1-115">静的な <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> メソッドを呼び出して新しい <xref:System.Security.Principal.WindowsIdentity> オブジェクトを初期化します。このメソッドは、現在の Windows アカウントに対してクエリを実行し、そのアカウントに関する情報を新規作成された ID オブジェクトに配置します。</span><span class="sxs-lookup"><span data-stu-id="722e1-115">Initialize a new <xref:System.Security.Principal.WindowsIdentity> object by calling the static <xref:System.Security.Principal.WindowsIdentity.GetCurrent%2A?displayProperty=nameWithType> method, which queries the current Windows account and places information about that account into the newly created identity object.</span></span> <span data-ttu-id="722e1-116">次のコードは、<xref:System.Security.Principal.WindowsIdentity> オブジェクトを新規作成し、これを現在の認証済みユーザーに初期化します。</span><span class="sxs-lookup"><span data-stu-id="722e1-116">The following code creates a new <xref:System.Security.Principal.WindowsIdentity> object and initializes it to the current authenticated user.</span></span>  
  
    ```csharp  
    WindowsIdentity MyIdentity = WindowsIdentity.GetCurrent();  
    ```  
  
    ```vb  
    Dim MyIdentity As WindowsIdentity = WindowsIdentity.GetCurrent()  
    ```  
  
2.  <span data-ttu-id="722e1-117"><xref:System.Security.Principal.WindowsPrincipal> オブジェクトを新規作成し、これに前の手順で作成された <xref:System.Security.Principal.WindowsIdentity> オブジェクトの値を渡します。</span><span class="sxs-lookup"><span data-stu-id="722e1-117">Create a new <xref:System.Security.Principal.WindowsPrincipal> object and pass it the value of the <xref:System.Security.Principal.WindowsIdentity> object created in the preceding step.</span></span>  
  
    ```csharp  
    WindowsPrincipal MyPrincipal = new WindowsPrincipal(MyIdentity);  
    ```  
  
    ```vb  
    Dim MyPrincipal As New WindowsPrincipal(MyIdentity)  
    ```  
  
3.  <span data-ttu-id="722e1-118">プリンシパル オブジェクトが作成されると、いくつかのメソッドのいずれかを使用して検証できます。</span><span class="sxs-lookup"><span data-stu-id="722e1-118">When the principal object has been created, you can use one of several methods to validate it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="722e1-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="722e1-119">See Also</span></span>  
 [<span data-ttu-id="722e1-120">プリンシパル オブジェクトと ID オブジェクト</span><span class="sxs-lookup"><span data-stu-id="722e1-120">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
