---
title: "アセンブリを作成できません:&lt;エラー メッセージ&gt;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords: BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9dcf3d4bec379faa5783ca17847b91f9739df598
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="unable-to-emit-assembly-lterror-messagegt"></a><span data-ttu-id="0e39e-102">アセンブリを作成できません:&lt;エラー メッセージ&gt;</span><span class="sxs-lookup"><span data-stu-id="0e39e-102">Unable to emit assembly: &lt;error message&gt;</span></span>
<span data-ttu-id="0e39e-103">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] コンパイラは、マニフェストを伴うアセンブリを生成するためにアセンブリ リンカー (Al.exe、Alink とも呼ばれます) を呼び出しますが、アセンブリを生成する出力段階でリンカーからエラーが報告されます。</span><span class="sxs-lookup"><span data-stu-id="0e39e-103">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest, with the linker reporting an error in the emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="0e39e-104">**エラー ID:** BC30145</span><span class="sxs-lookup"><span data-stu-id="0e39e-104">**Error ID:** BC30145</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0e39e-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="0e39e-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="0e39e-106">引用されているエラー メッセージを調べ、「 [Al.exe ツールのエラーと警告](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) 」というトピックで、より詳細な説明とアドバイスを参照します。</span><span class="sxs-lookup"><span data-stu-id="0e39e-106">Examine the quoted error message and consult the topic [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) for further explanation and advice.</span></span>  
  
2.  <span data-ttu-id="0e39e-107">アセンブリに手動で署名するかを使用して再試行してください、 [Al.exe (アセンブリ リンカー)](https://msdn.microsoft.com/library/c405shex)または[Sn.exe (厳密名ツール)](https://msdn.microsoft.com/library/k5b5tt23)です。</span><span class="sxs-lookup"><span data-stu-id="0e39e-107">Try signing the assembly manually, using either the [Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) or the [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span></span>  
  
3.  <span data-ttu-id="0e39e-108">エラーが続く場合は、状況に関する情報を収集し、マイクロソフト プロダクト サポート サービスに通知してください。</span><span class="sxs-lookup"><span data-stu-id="0e39e-108">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="0e39e-109">アセンブリを手動で署名するには</span><span class="sxs-lookup"><span data-stu-id="0e39e-109">To sign the assembly manually</span></span>  
  
1.  <span data-ttu-id="0e39e-110">使用して、 [Sn.exe (厳密名ツール)](https://msdn.microsoft.com/library/k5b5tt23)公開/秘密キー ペア ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="0e39e-110">Use the [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23) to create a public/private key pair file.</span></span>  
  
     <span data-ttu-id="0e39e-111">このファイルは .snk の拡張子を持ちます。</span><span class="sxs-lookup"><span data-stu-id="0e39e-111">This file has a .snk extension.</span></span>  
  
2.  <span data-ttu-id="0e39e-112">エラーが発生している COM 参照をプロジェクトから削除します。</span><span class="sxs-lookup"><span data-stu-id="0e39e-112">Delete the COM reference that is generating the error from your project.</span></span>  
  
3.  <span data-ttu-id="0e39e-113">Windows から**開始** メニューのをポイント**プログラム**、 をポイント**Microsoft Visual Studio 2008**、 をポイント**Visual Studio Tools**、およびをクリックして**Visual Studio 2008 コマンド プロンプト**です。</span><span class="sxs-lookup"><span data-stu-id="0e39e-113">From the Windows **Start** menu, point to **Programs**, point to **Microsoft Visual Studio 2008**, point to **Visual Studio Tools**, and then click **Visual Studio 2008 Command Prompt**.</span></span>  
  
4.  <span data-ttu-id="0e39e-114">アセンブリ ラッパーを格納するディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="0e39e-114">Move to the directory where you want to place your assembly wrapper.</span></span>  
  
5.  <span data-ttu-id="0e39e-115">次のコードを入力します。</span><span class="sxs-lookup"><span data-stu-id="0e39e-115">Type the following code.</span></span>  
  
    ```  
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>  
    ```  
  
     <span data-ttu-id="0e39e-116">コードの一例として、次のように入力することができます。</span><span class="sxs-lookup"><span data-stu-id="0e39e-116">An example of the code you might enter would be the following.</span></span>  
  
    ```  
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"  
    ```  
  
     <span data-ttu-id="0e39e-117">パスやファイルに空白が含まれている場合には、二重引用符 (") を使用します。</span><span class="sxs-lookup"><span data-stu-id="0e39e-117">Use double quotation marks (") if a path or file contains spaces.</span></span>  
  
6.  <span data-ttu-id="0e39e-118">[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] で、作成したファイルに .NET アセンブリへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="0e39e-118">In [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], add a .NET Assembly reference to the file you just created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e39e-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="0e39e-119">See Also</span></span>  
 [<span data-ttu-id="0e39e-120">Al.exe (アセンブリ リンカー)</span><span class="sxs-lookup"><span data-stu-id="0e39e-120">Al.exe (Assembly Linker)</span></span>](https://msdn.microsoft.com/library/c405shex)  
 [<span data-ttu-id="0e39e-121">Al.exe ツールのエラーと警告</span><span class="sxs-lookup"><span data-stu-id="0e39e-121">Al.exe Tool Errors and Warnings</span></span>](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)  
 [<span data-ttu-id="0e39e-122">Sn.exe (厳密名ツール)</span><span class="sxs-lookup"><span data-stu-id="0e39e-122">Sn.exe (Strong Name Tool)</span></span>](https://msdn.microsoft.com/library/k5b5tt23)  
 [<span data-ttu-id="0e39e-123">方法: 公開キーと秘密キーのキー ペアを作成する</span><span class="sxs-lookup"><span data-stu-id="0e39e-123">How to: Create a Public-Private Key Pair</span></span>](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114)  
 [<span data-ttu-id="0e39e-124">ご意見</span><span class="sxs-lookup"><span data-stu-id="0e39e-124">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
