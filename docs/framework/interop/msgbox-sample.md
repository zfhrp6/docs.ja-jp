---
title: "MsgBox のサンプル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- marshaling, MsgBox sample
- data marshaling, MsgBox sample
ms.assetid: 9e0edff6-cc0d-4d5c-a445-aecf283d9c3a
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0d9be3d490a687541a0b1c7af3d90c52523413a5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="msgbox-sample"></a><span data-ttu-id="37e52-102">MsgBox のサンプル</span><span class="sxs-lookup"><span data-stu-id="37e52-102">MsgBox Sample</span></span>
<span data-ttu-id="37e52-103">このサンプルでは、文字列型を In パラメーターとして値渡しする方法と、<xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>、<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>、および <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> の各フィールドを使用する場合について説明します。</span><span class="sxs-lookup"><span data-stu-id="37e52-103">This sample demonstrates how to pass string types by value as In parameters and when to use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>, <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>, and <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> fields.</span></span>  
  
 <span data-ttu-id="37e52-104">MsgBox のサンプルで使用するアンマネージ関数とその関数宣言を次に示します。</span><span class="sxs-lookup"><span data-stu-id="37e52-104">The MsgBox sample uses the following unmanaged function, shown with its original function declaration:</span></span>  
  
-   <span data-ttu-id="37e52-105">User32.dll からエクスポートされる **MessageBox**。</span><span class="sxs-lookup"><span data-stu-id="37e52-105">**MessageBox** exported from User32.dll.</span></span>  
  
    ```  
    int MessageBox(HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption,   
       UINT uType);  
    ```  
  
 <span data-ttu-id="37e52-106">このサンプルでは、`LibWrap` クラスの中には、`MsgBoxSample` クラスによって呼び出される各アンマネージ関数に関するマネージ プロトタイプが含まれます。</span><span class="sxs-lookup"><span data-stu-id="37e52-106">In this sample, the `LibWrap` class contains a managed prototype for each unmanaged function called by the `MsgBoxSample` class.</span></span> <span data-ttu-id="37e52-107">マネージ プロトタイプ メソッドの `MsgBox`、`MsgBox2`、および `MsgBox3` は、同じアンマネージ関数に対して異なる宣言を持ちます。</span><span class="sxs-lookup"><span data-stu-id="37e52-107">The managed prototype methods `MsgBox`, `MsgBox2`, and `MsgBox3` have different declarations for the same unmanaged function.</span></span>  
  
 <span data-ttu-id="37e52-108">`MsgBox2` に対する宣言により、メッセージ ボックス内に不正な出力が生成されます。その原因は、ANSI として指定した文字型が、Unicode 関数の名前であるエントリ ポイント `MessageBoxW` と一致しないからです。</span><span class="sxs-lookup"><span data-stu-id="37e52-108">The declaration for `MsgBox2` produces incorrect output in the message box because the character type, specified as ANSI, is mismatched with the entry point `MessageBoxW`, which is the name of the Unicode function.</span></span> <span data-ttu-id="37e52-109">`MsgBox3` に対する宣言により、**EntryPoint**、**CharSet**、および **ExactSpelling** の各フィールド間に不一致が発生します。</span><span class="sxs-lookup"><span data-stu-id="37e52-109">The declaration for `MsgBox3` creates a mismatch between the **EntryPoint**, **CharSet**, and **ExactSpelling** fields.</span></span> <span data-ttu-id="37e52-110">`MsgBox3` を呼び出すと例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="37e52-110">When called, `MsgBox3` throws an exception.</span></span> <span data-ttu-id="37e52-111">文字列の名前付けと名前のマーシャリングの詳細については、「[文字セットの指定](../../../docs/framework/interop/specifying-a-character-set.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="37e52-111">For detailed information on string naming and name marshaling, see [Specifying a Character Set](../../../docs/framework/interop/specifying-a-character-set.md).</span></span>  
  
## <a name="declaring-prototypes"></a><span data-ttu-id="37e52-112">プロトタイプの宣言</span><span class="sxs-lookup"><span data-stu-id="37e52-112">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#5)]
 [!code-csharp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#5)]
 [!code-vb[Conceptual.Interop.Marshaling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#5)]  
  
## <a name="calling-functions"></a><span data-ttu-id="37e52-113">関数の呼び出し</span><span class="sxs-lookup"><span data-stu-id="37e52-113">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#6)]
 [!code-csharp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#6)]
 [!code-vb[Conceptual.Interop.Marshaling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="37e52-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="37e52-114">See Also</span></span>  
 [<span data-ttu-id="37e52-115">マーシャリング (文字列の)</span><span class="sxs-lookup"><span data-stu-id="37e52-115">Marshaling Strings</span></span>](../../../docs/framework/interop/marshaling-strings.md)  
 [<span data-ttu-id="37e52-116">プラットフォーム呼び出しのデータ型</span><span class="sxs-lookup"><span data-stu-id="37e52-116">Platform Invoke Data Types</span></span>](http://msdn.microsoft.com/en-us/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [<span data-ttu-id="37e52-117">文字列に対する既定のマーシャリング</span><span class="sxs-lookup"><span data-stu-id="37e52-117">Default Marshaling for Strings</span></span>](../../../docs/framework/interop/default-marshaling-for-strings.md)  
 [<span data-ttu-id="37e52-118">マネージ コードでのプロトタイプの作成</span><span class="sxs-lookup"><span data-stu-id="37e52-118">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [<span data-ttu-id="37e52-119">文字セットの指定</span><span class="sxs-lookup"><span data-stu-id="37e52-119">Specifying a Character Set</span></span>](../../../docs/framework/interop/specifying-a-character-set.md)
