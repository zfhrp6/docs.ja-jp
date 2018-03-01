---
title: "アセンブリ マニフェストを作成中にエラー:&lt;エラー メッセージ&gt;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5e88d28ef787eb57b71d94f4ee51c09e9751dbff
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="error-creating-assembly-manifest-lterror-messagegt"></a><span data-ttu-id="cc888-102">アセンブリ マニフェストを作成中にエラー:&lt;エラー メッセージ&gt;</span><span class="sxs-lookup"><span data-stu-id="cc888-102">Error creating assembly manifest: &lt;error message&gt;</span></span>
<span data-ttu-id="cc888-103">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] コンパイラはアセンブリ リンカー (Al.exe、Alink とも呼ばれる) を呼び出し、マニフェストを伴うアセンブリを生成します。</span><span class="sxs-lookup"><span data-stu-id="cc888-103">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="cc888-104">リンカーが、アセンブリの生成前の段階でのエラーを報告しています。</span><span class="sxs-lookup"><span data-stu-id="cc888-104">The linker has reported an error in the pre-emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="cc888-105">指定したキー ファイルまたはキー コンテナーに原因がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="cc888-105">This can occur if there are problems with the key file or the key container specified.</span></span> <span data-ttu-id="cc888-106">アセンブリに完全署名するには、公開キーと秘密キーに関する情報を含む有効なキー ファイルを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc888-106">To fully sign an assembly, you must provide a valid key file that contains information about the public and private keys.</span></span> <span data-ttu-id="cc888-107">アセンブリに遅延署名するには、**[遅延署名のみ]** チェック ボックスをオンにし、公開キー情報を含む有効なキー ファイルを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc888-107">To delay sign an assembly, you must select the **Delay sign only** check box and provide a valid key file that contains information about the public key information.</span></span> <span data-ttu-id="cc888-108">アセンブリに遅延署名する場合、秘密キーは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="cc888-108">The private key is not necessary when an assembly is delay-signed.</span></span> <span data-ttu-id="cc888-109">詳しくは、「[方法 : 厳密な名前でアセンブリに署名する](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cc888-109">For more information, see [How to: Sign an Assembly with a Strong Name](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).</span></span>  
  
 <span data-ttu-id="cc888-110">**エラー ID:** BC30140</span><span class="sxs-lookup"><span data-stu-id="cc888-110">**Error ID:** BC30140</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cc888-111">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="cc888-111">To correct this error</span></span>  
  
1.  <span data-ttu-id="cc888-112">引用符で囲まれたエラー メッセージを確認し、トピックを参照して[Al.exe](../../../framework/tools/al-exe-assembly-linker.md)です。</span><span class="sxs-lookup"><span data-stu-id="cc888-112">Examine the quoted error message and consult the topic [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span> <span data-ttu-id="cc888-113">エラー AL1019 説明とアドバイスを参照</span><span class="sxs-lookup"><span data-stu-id="cc888-113">for error AL1019 further explanation and advice</span></span>  
  
2.  <span data-ttu-id="cc888-114">エラーが続く場合は、状況に関する情報を収集し、マイクロソフト プロダクト サポート サービスに通知してください。</span><span class="sxs-lookup"><span data-stu-id="cc888-114">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc888-115">参照</span><span class="sxs-lookup"><span data-stu-id="cc888-115">See Also</span></span>  
 [<span data-ttu-id="cc888-116">方法: 厳密な名前でアセンブリに署名する</span><span class="sxs-lookup"><span data-stu-id="cc888-116">How to: Sign an Assembly with a Strong Name</span></span>](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 <span data-ttu-id="cc888-117">[[署名] ページ (プロジェクト デザイナー)](/visualstudio/ide/reference/signing-page-project-designer)</span><span class="sxs-lookup"><span data-stu-id="cc888-117">[Signing Page, Project Designer](/visualstudio/ide/reference/signing-page-project-designer)</span></span>  
 <span data-ttu-id="cc888-118">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md)です。</span><span class="sxs-lookup"><span data-stu-id="cc888-118">[Al.exe](../../../framework/tools/al-exe-assembly-linker.md).</span></span>  
 [<span data-ttu-id="cc888-119">ご意見</span><span class="sxs-lookup"><span data-stu-id="cc888-119">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
