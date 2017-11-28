---
title: "アセンブリ マニフェストを作成中にエラー:&lt;エラー メッセージ&gt;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords: BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d846ef88f0c36b49e79b9d11252fcef419dfa0ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="error-creating-assembly-manifest-lterror-messagegt"></a><span data-ttu-id="38286-102">アセンブリ マニフェストを作成中にエラー:&lt;エラー メッセージ&gt;</span><span class="sxs-lookup"><span data-stu-id="38286-102">Error creating assembly manifest: &lt;error message&gt;</span></span>
<span data-ttu-id="38286-103">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] コンパイラはアセンブリ リンカー (Al.exe、Alink とも呼ばれる) を呼び出し、マニフェストを伴うアセンブリを生成します。</span><span class="sxs-lookup"><span data-stu-id="38286-103">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest.</span></span> <span data-ttu-id="38286-104">リンカーが、アセンブリの生成前の段階でのエラーを報告しています。</span><span class="sxs-lookup"><span data-stu-id="38286-104">The linker has reported an error in the pre-emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="38286-105">指定したキー ファイルまたはキー コンテナーに原因がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="38286-105">This can occur if there are problems with the key file or the key container specified.</span></span> <span data-ttu-id="38286-106">アセンブリに完全署名するには、公開キーと秘密キーに関する情報を含む有効なキー ファイルを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="38286-106">To fully sign an assembly, you must provide a valid key file that contains information about the public and private keys.</span></span> <span data-ttu-id="38286-107">アセンブリに遅延署名するには、**[遅延署名のみ]** チェック ボックスをオンにし、公開キー情報を含む有効なキー ファイルを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="38286-107">To delay sign an assembly, you must select the **Delay sign only** check box and provide a valid key file that contains information about the public key information.</span></span> <span data-ttu-id="38286-108">アセンブリに遅延署名する場合、秘密キーは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="38286-108">The private key is not necessary when an assembly is delay-signed.</span></span> <span data-ttu-id="38286-109">詳細については、次を参照してください。[する方法: アセンブリ (Visual Studio) に署名](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564)です。</span><span class="sxs-lookup"><span data-stu-id="38286-109">For more information, see [How to: Sign an Assembly (Visual Studio)](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564).</span></span>  
  
 <span data-ttu-id="38286-110">**エラー ID:** BC30140</span><span class="sxs-lookup"><span data-stu-id="38286-110">**Error ID:** BC30140</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="38286-111">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="38286-111">To correct this error</span></span>  
  
1.  <span data-ttu-id="38286-112">引用符で囲まれたエラー メッセージを確認し、トピックを参照して[Al.exe ツールのエラーと警告](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)エラー AL1019 の説明とアドバイスをさらに</span><span class="sxs-lookup"><span data-stu-id="38286-112">Examine the quoted error message and consult the topic [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) for error AL1019 further explanation and advice</span></span>  
  
2.  <span data-ttu-id="38286-113">エラーが続く場合は、状況に関する情報を収集し、マイクロソフト プロダクト サポート サービスに通知してください。</span><span class="sxs-lookup"><span data-stu-id="38286-113">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38286-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="38286-114">See Also</span></span>  
 [<span data-ttu-id="38286-115">方法: アセンブリに署名する (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="38286-115">How to: Sign an Assembly (Visual Studio)</span></span>](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564)  
 <span data-ttu-id="38286-116">[[署名] ページ (プロジェクト デザイナー)](/visualstudio/ide/reference/signing-page-project-designer)</span><span class="sxs-lookup"><span data-stu-id="38286-116">[Signing Page, Project Designer](/visualstudio/ide/reference/signing-page-project-designer)</span></span>  
 [<span data-ttu-id="38286-117">Al.exe (アセンブリ リンカー)</span><span class="sxs-lookup"><span data-stu-id="38286-117">Al.exe (Assembly Linker)</span></span>](https://msdn.microsoft.com/library/c405shex)  
 [<span data-ttu-id="38286-118">Al.exe ツールのエラーと警告</span><span class="sxs-lookup"><span data-stu-id="38286-118">Al.exe Tool Errors and Warnings</span></span>](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)  
 [<span data-ttu-id="38286-119">ご意見</span><span class="sxs-lookup"><span data-stu-id="38286-119">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
