---
title: "アセンブリ マニフェストを作成中にエラー:&lt;エラー メッセージ&gt;|Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30140
- vbc30140
dev_langs:
- VB
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
caps.latest.revision: 13
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
ms.openlocfilehash: 12e08feff09e901839c4e282d32a0a4e54e12576
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="error-creating-assembly-manifest-lterror-messagegt"></a><span data-ttu-id="f62d2-102">アセンブリ マニフェストを作成中にエラー:&lt;エラー メッセージ&gt;</span><span class="sxs-lookup"><span data-stu-id="f62d2-102">Error creating assembly manifest: &lt;error message&gt;</span></span>
<span data-ttu-id="f62d2-103">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] コンパイラはアセンブリ リンカー (Al.exe、Alink とも呼ばれる) を呼び出し、マニフェストを伴うアセンブリを生成します。</span><span class="sxs-lookup"><span data-stu-id="f62d2-103">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="f62d2-104">リンカーが、アセンブリの生成前の段階でのエラーを報告しています。</span><span class="sxs-lookup"><span data-stu-id="f62d2-104">The linker has reported an error in the pre-emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="f62d2-105">指定したキー ファイルまたはキー コンテナーに原因がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="f62d2-105">This can occur if there are problems with the key file or the key container specified.</span></span> <span data-ttu-id="f62d2-106">アセンブリに完全署名するには、公開キーと秘密キーに関する情報を含む有効なキー ファイルを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f62d2-106">To fully sign an assembly, you must provide a valid key file that contains information about the public and private keys.</span></span> <span data-ttu-id="f62d2-107">アセンブリの署名を遅らせるには、選択、**遅延署名のみ**チェック ボックスをオンし、公開キー情報に関する情報を含む有効なキー ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="f62d2-107">To delay sign an assembly, you must select the **Delay sign only** check box and provide a valid key file that contains information about the public key information.</span></span> <span data-ttu-id="f62d2-108">アセンブリに遅延署名する場合、秘密キーは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="f62d2-108">The private key is not necessary when an assembly is delay-signed.</span></span> <span data-ttu-id="f62d2-109">詳細については、次を参照してください。[方法: アセンブリ (Visual Studio) に署名](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564)します。</span><span class="sxs-lookup"><span data-stu-id="f62d2-109">For more information, see [How to: Sign an Assembly (Visual Studio)](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564).</span></span>  
  
 <span data-ttu-id="f62d2-110">**エラー ID:** BC30140</span><span class="sxs-lookup"><span data-stu-id="f62d2-110">**Error ID:** BC30140</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f62d2-111">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="f62d2-111">To correct this error</span></span>  
  
1.  <span data-ttu-id="f62d2-112">引用符で囲まれたエラー メッセージを調べ、トピックを参照してください[Al.exe ツールのエラーと警告](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)エラー AL1019 説明とアドバイスに詳しく。</span><span class="sxs-lookup"><span data-stu-id="f62d2-112">Examine the quoted error message and consult the topic [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) for error AL1019 further explanation and advice</span></span>  
  
2.  <span data-ttu-id="f62d2-113">エラーが続く場合は、状況に関する情報を収集し、マイクロソフト プロダクト サポート サービスに通知してください。</span><span class="sxs-lookup"><span data-stu-id="f62d2-113">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f62d2-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="f62d2-114">See Also</span></span>  
 <span data-ttu-id="f62d2-115">[方法: アセンブリに署名する (Visual Studio)](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564) </span><span class="sxs-lookup"><span data-stu-id="f62d2-115">[How to: Sign an Assembly (Visual Studio)](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564) </span></span>  
<span data-ttu-id="f62d2-116"> [[署名] ページ (プロジェクト デザイナー)](https://docs.microsoft.com/visualstudio/ide/reference/signing-page-project-designer) </span><span class="sxs-lookup"><span data-stu-id="f62d2-116"> [Signing Page, Project Designer](https://docs.microsoft.com/visualstudio/ide/reference/signing-page-project-designer) </span></span>  
<span data-ttu-id="f62d2-117"> [Al.exe (アセンブリ リンカー)](https://msdn.microsoft.com/library/c405shex) </span><span class="sxs-lookup"><span data-stu-id="f62d2-117"> [Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) </span></span>  
<span data-ttu-id="f62d2-118"> [Al.exe ツールのエラーと警告](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) </span><span class="sxs-lookup"><span data-stu-id="f62d2-118"> [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) </span></span>  
<span data-ttu-id="f62d2-119"> [ご意見](https://docs.microsoft.com/visualstudio/ide/talk-to-us)</span><span class="sxs-lookup"><span data-stu-id="f62d2-119"> [Talk to Us](https://docs.microsoft.com/visualstudio/ide/talk-to-us)</span></span>
