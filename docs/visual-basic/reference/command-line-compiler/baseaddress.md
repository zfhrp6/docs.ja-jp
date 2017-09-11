---
title: "/baseaddress |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /baseaddress
- baseaddress
dev_langs:
- VB
helpviewer_keywords:
- -baseaddress compiler option [Visual Basic]
- /baseaddress compiler option [Visual Basic]
- baseaddress compiler option [Visual Basic]
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
caps.latest.revision: 16
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 5687f119a57e0e54eca4df8f91fdf5e8b2775f82
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="baseaddress"></a><span data-ttu-id="dabf4-102">/baseaddress</span><span class="sxs-lookup"><span data-stu-id="dabf4-102">/baseaddress</span></span>
<span data-ttu-id="dabf4-103">DLL を作成するときに、既定のベース アドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="dabf4-103">Specifies a default base address when creating a DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dabf4-104">構文</span><span class="sxs-lookup"><span data-stu-id="dabf4-104">Syntax</span></span>  
  
```  
/baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="dabf4-105">引数</span><span class="sxs-lookup"><span data-stu-id="dabf4-105">Arguments</span></span>  
  
|<span data-ttu-id="dabf4-106">用語</span><span class="sxs-lookup"><span data-stu-id="dabf4-106">Term</span></span>|<span data-ttu-id="dabf4-107">定義</span><span class="sxs-lookup"><span data-stu-id="dabf4-107">Definition</span></span>|  
|---|---|  
|`address`|<span data-ttu-id="dabf4-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="dabf4-108">Required.</span></span> <span data-ttu-id="dabf4-109">DLL のベース アドレス。</span><span class="sxs-lookup"><span data-stu-id="dabf4-109">The base address for the DLL.</span></span> <span data-ttu-id="dabf4-110">このアドレスは、16 進数として指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dabf4-110">This address must be specified as a hexadecimal number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dabf4-111">コメント</span><span class="sxs-lookup"><span data-stu-id="dabf4-111">Remarks</span></span>  
 <span data-ttu-id="dabf4-112">によって、DLL の既定のベース アドレスを設定、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="dabf4-112">The default base address for a DLL is set by the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].</span></span>  
  
 <span data-ttu-id="dabf4-113">このアドレスの下位ワードが丸められることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="dabf4-113">Be aware that the lower-order word in this address is rounded.</span></span> <span data-ttu-id="dabf4-114">たとえば、0x11110001 とを指定する場合はられて 0x11110000 に丸められます。</span><span class="sxs-lookup"><span data-stu-id="dabf4-114">For example, if you specify 0x11110001, it is rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="dabf4-115">DLL の署名プロセスを完了するには、`–R`厳密名ツール (Sn.exe) のオプションです。</span><span class="sxs-lookup"><span data-stu-id="dabf4-115">To complete the signing process for a DLL, use the `–R` option of the Strong Naming tool (Sn.exe).</span></span>  
  
 <span data-ttu-id="dabf4-116">ターゲットが DLL ではない場合、このオプションは無視されます。</span><span class="sxs-lookup"><span data-stu-id="dabf4-116">This option is ignored if the target is not a DLL.</span></span>  
  
|<span data-ttu-id="dabf4-117">Visual Studio IDE で/baseaddress を設定するには</span><span class="sxs-lookup"><span data-stu-id="dabf4-117">To set /baseaddress in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="dabf4-118">1.**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="dabf4-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="dabf4-119">**プロジェクト** メニューのをクリックして**プロパティ**します。</span><span class="sxs-lookup"><span data-stu-id="dabf4-119">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="dabf4-120">詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dabf4-120">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="dabf4-121">2.**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="dabf4-121">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="dabf4-122">3.[ **詳細設定**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dabf4-122">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="dabf4-123">4.値を変更、 **DLL のベース アドレス:**ボックス。</span><span class="sxs-lookup"><span data-stu-id="dabf4-123">4.  Modify the value in the **DLL base address:** box.</span></span> <span data-ttu-id="dabf4-124">**注:** 、 **DLL のベース アドレス:**ターゲットが DLL でない限り、ボックスは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="dabf4-124">**Note:**      The **DLL base address:** box is read-only unless the target is a DLL.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dabf4-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="dabf4-125">See Also</span></span>  
 <span data-ttu-id="dabf4-126">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="dabf4-126">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="dabf4-127"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span><span class="sxs-lookup"><span data-stu-id="dabf4-127"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span></span>  
<span data-ttu-id="dabf4-128"> [コンパイル コマンドラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="dabf4-128"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="dabf4-129"> [Sn.exe (厳密名ツール)](https://msdn.microsoft.com/library/k5b5tt23)</span><span class="sxs-lookup"><span data-stu-id="dabf4-129"> [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23)</span></span>
