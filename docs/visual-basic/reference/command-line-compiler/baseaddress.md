---
title: /baseaddress
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- /baseaddress
- baseaddress
helpviewer_keywords:
- -baseaddress compiler option [Visual Basic]
- /baseaddress compiler option [Visual Basic]
- baseaddress compiler option [Visual Basic]
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1ad39acdec92667fbb0848a1c64c567b504dcb67
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="baseaddress"></a><span data-ttu-id="245b4-102">/baseaddress</span><span class="sxs-lookup"><span data-stu-id="245b4-102">/baseaddress</span></span>
<span data-ttu-id="245b4-103">DLL を作成するときに、既定のベース アドレスを指定します。</span><span class="sxs-lookup"><span data-stu-id="245b4-103">Specifies a default base address when creating a DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="245b4-104">構文</span><span class="sxs-lookup"><span data-stu-id="245b4-104">Syntax</span></span>  
  
```  
/baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="245b4-105">引数</span><span class="sxs-lookup"><span data-stu-id="245b4-105">Arguments</span></span>  
  
|<span data-ttu-id="245b4-106">用語</span><span class="sxs-lookup"><span data-stu-id="245b4-106">Term</span></span>|<span data-ttu-id="245b4-107">定義</span><span class="sxs-lookup"><span data-stu-id="245b4-107">Definition</span></span>|  
|---|---|  
|`address`|<span data-ttu-id="245b4-108">必須。</span><span class="sxs-lookup"><span data-stu-id="245b4-108">Required.</span></span> <span data-ttu-id="245b4-109">DLL のベース アドレス。</span><span class="sxs-lookup"><span data-stu-id="245b4-109">The base address for the DLL.</span></span> <span data-ttu-id="245b4-110">このアドレスは、16 進数として指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="245b4-110">This address must be specified as a hexadecimal number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="245b4-111">コメント</span><span class="sxs-lookup"><span data-stu-id="245b4-111">Remarks</span></span>  
 <span data-ttu-id="245b4-112">によって、DLL の既定のベース アドレスを設定、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="245b4-112">The default base address for a DLL is set by the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
 <span data-ttu-id="245b4-113">このアドレスの下位ワードが丸められることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="245b4-113">Be aware that the lower-order word in this address is rounded.</span></span> <span data-ttu-id="245b4-114">たとえば、0x11110001 とを指定する場合はられて 0x11110000 に丸められます。</span><span class="sxs-lookup"><span data-stu-id="245b4-114">For example, if you specify 0x11110001, it is rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="245b4-115">DLL の署名プロセスを完了するには、`–R`厳密名ツール (Sn.exe) のオプションです。</span><span class="sxs-lookup"><span data-stu-id="245b4-115">To complete the signing process for a DLL, use the `–R` option of the Strong Naming tool (Sn.exe).</span></span>  
  
 <span data-ttu-id="245b4-116">ターゲットが DLL ではない場合、このオプションは無視されます。</span><span class="sxs-lookup"><span data-stu-id="245b4-116">This option is ignored if the target is not a DLL.</span></span>  
  
|<span data-ttu-id="245b4-117">Visual Studio IDE で/baseaddress を設定するには</span><span class="sxs-lookup"><span data-stu-id="245b4-117">To set /baseaddress in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="245b4-118">1.**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="245b4-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="245b4-119">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="245b4-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="245b4-120">2.**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="245b4-120">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="245b4-121">3.**[詳細設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="245b4-121">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="245b4-122">4.値を変更、 **DLL ベース アドレス:**ボックス。</span><span class="sxs-lookup"><span data-stu-id="245b4-122">4.  Modify the value in the **DLL base address:** box.</span></span> <span data-ttu-id="245b4-123">**注:** 、 **DLL ベース アドレス:**ターゲットが DLL でない限りボックスは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="245b4-123">**Note:**      The **DLL base address:** box is read-only unless the target is a DLL.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="245b4-124">参照</span><span class="sxs-lookup"><span data-stu-id="245b4-124">See Also</span></span>  
 [<span data-ttu-id="245b4-125">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="245b4-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="245b4-126">/target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="245b4-126">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="245b4-127">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="245b4-127">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 <span data-ttu-id="245b4-128">[Sn.exe (厳密名ツール)][Sn.exe (厳密名ツール)](../../../framework/tools/sn-exe-strong-name-tool.md))</span><span class="sxs-lookup"><span data-stu-id="245b4-128">[Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md))</span></span>
