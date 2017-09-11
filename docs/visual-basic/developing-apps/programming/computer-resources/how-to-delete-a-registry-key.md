---
title: "方法: レジストリ キーを削除する (Visual Basic)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.DeleteSetting
dev_langs:
- VB
helpviewer_keywords:
- GetSetting function
- registry, deleting values
- GetAllSettings function
- registry keys, deleting
- registry, deleting keys
- examples [Visual Basic], registry
ms.assetid: ab9aca0e-42b0-4ff7-8ff9-845a4bfdf9f2
caps.latest.revision: 28
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0fc37aff9f6a0ae3a7953377ebf95179d01bb693
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-delete-a-registry-key-in-visual-basic"></a><span data-ttu-id="e3520-102">方法: レジストリ キーを削除する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3520-102">How to: Delete a Registry Key in Visual Basic</span></span>
<span data-ttu-id="e3520-103"><xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> メソッドと <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> メソッドはレジストリ キーの削除に使用できます。</span><span class="sxs-lookup"><span data-stu-id="e3520-103">The <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> and <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> methods can be used to delete registry keys.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="e3520-104">プロシージャ</span><span class="sxs-lookup"><span data-stu-id="e3520-104">Procedure</span></span>  
  
#### <a name="to-delete-a-registry-key"></a><span data-ttu-id="e3520-105">レジストリ キーを削除するには</span><span class="sxs-lookup"><span data-stu-id="e3520-105">To delete a registry key</span></span>  
  
-   <span data-ttu-id="e3520-106">`DeleteSubKey` メソッドを使用して、レジストリ キーを削除します。</span><span class="sxs-lookup"><span data-stu-id="e3520-106">Use the `DeleteSubKey` method to delete a registry key.</span></span> <span data-ttu-id="e3520-107">この例では、CurrentUser ハイブの Software/TestApp キーを削除します。</span><span class="sxs-lookup"><span data-stu-id="e3520-107">This example deletes the key Software/TestApp in the CurrentUser hive.</span></span> <span data-ttu-id="e3520-108">このキーは、コード内で適切な文字列に変更したり、ユーザーが指定した情報を使用したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="e3520-108">You can change this in the code to the appropriate string, or have it rely on user-supplied information.</span></span>  
  
     <span data-ttu-id="e3520-109">[!code-vb[VbResourceTasks#19](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-delete-a-registry-key_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="e3520-109">[!code-vb[VbResourceTasks#19](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-delete-a-registry-key_1.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e3520-110">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="e3520-110">Robust Programming</span></span>  
 <span data-ttu-id="e3520-111">キーと値の組み合わせが存在しない場合、`DeleteSubKey` メソッドは空の文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="e3520-111">The `DeleteSubKey` method returns an empty string if the key/value pair does not exist.</span></span>  
  
 <span data-ttu-id="e3520-112">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e3520-112">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="e3520-113">キーの名前が `Nothing` である場合 (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="e3520-113">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="e3520-114">レジストリ キーを作成するためのアクセス許可がユーザーにない場合 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="e3520-114">The user does not have permissions to delete registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="e3520-115">キー名が 255 文字の制限を超えている場合 (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="e3520-115">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="e3520-116">レジストリ キーが読み取り専用の場合 (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="e3520-116">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="e3520-117">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="e3520-117">.NET Framework Security</span></span>  
 <span data-ttu-id="e3520-118">必要なアクセス許可が実行時に与えられない (<xref:System.Security.Permissions.RegistryPermission>) 場合、またはユーザーが設定の作成や書き込みを行うための適切な (ACL によって決定された) アクセス権を持っていない場合、レジストリ呼び出しは失敗します。</span><span class="sxs-lookup"><span data-stu-id="e3520-118">Registry calls fail if either sufficient run-time permissions are not granted (<xref:System.Security.Permissions.RegistryPermission>) or if the user does not have the correct access (as determined by the ACLs) for creating or writing to settings.</span></span> <span data-ttu-id="e3520-119">たとえば、コード アクセス セキュリティのアクセス許可を持つローカル アプリケーションには、オペレーティング システムのアクセス許可がない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e3520-119">For example, a local application that has the code access security permission might not have operating system permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3520-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="e3520-120">See Also</span></span>  
 <span data-ttu-id="e3520-121"><xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A></span><span class="sxs-lookup"><span data-stu-id="e3520-121"><xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A></span></span>   
 <span data-ttu-id="e3520-122"><xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A></span><span class="sxs-lookup"><span data-stu-id="e3520-122"><xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A></span></span>   
 <span data-ttu-id="e3520-123"><xref:Microsoft.Win32.RegistryKey></span><span class="sxs-lookup"><span data-stu-id="e3520-123"><xref:Microsoft.Win32.RegistryKey></span></span>   
 <span data-ttu-id="e3520-124">[セキュリティとレジストリ](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md) </span><span class="sxs-lookup"><span data-stu-id="e3520-124">[Security and the Registry](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md) </span></span>  
 [<span data-ttu-id="e3520-125">レジストリからの読み取りとレジストリへの書き込み</span><span class="sxs-lookup"><span data-stu-id="e3520-125">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)

