---
title: "アセンブリを作成できません:&lt;エラー メッセージ&gt;|Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30145
- bc30145
dev_langs:
- VB
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
caps.latest.revision: 11
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
ms.openlocfilehash: d15981a1a2fb31ba377066fa421f5a9979d47a12
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="unable-to-emit-assembly-lterror-messagegt"></a><span data-ttu-id="04e78-102">アセンブリを作成できません:&lt;エラー メッセージ&gt;</span><span class="sxs-lookup"><span data-stu-id="04e78-102">Unable to emit assembly: &lt;error message&gt;</span></span>
<span data-ttu-id="04e78-103">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] コンパイラは、マニフェストを伴うアセンブリを生成するためにアセンブリ リンカー (Al.exe、Alink とも呼ばれます) を呼び出しますが、アセンブリを生成する出力段階でリンカーからエラーが報告されます。</span><span class="sxs-lookup"><span data-stu-id="04e78-103">The [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler calls the Assembly Linker (Al.exe, also known as Alink) to generate an assembly with a manifest, with the linker reporting an error in the emission stage of creating the assembly.</span></span>  
  
 <span data-ttu-id="04e78-104">**エラー ID:** BC30145</span><span class="sxs-lookup"><span data-stu-id="04e78-104">**Error ID:** BC30145</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="04e78-105">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="04e78-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="04e78-106">引用符で囲まれたエラー メッセージを調べ、トピックを参照してください。 [Al.exe ツールのエラーと警告](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)さらに詳しい説明とアドバイスします。</span><span class="sxs-lookup"><span data-stu-id="04e78-106">Examine the quoted error message and consult the topic [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) for further explanation and advice.</span></span>  
  
2.  <span data-ttu-id="04e78-107">アセンブリを手動で署名を使用してください、 [Al.exe (アセンブリ リンカー)](https://msdn.microsoft.com/library/c405shex)または[Sn.exe (厳密名ツール)](https://msdn.microsoft.com/library/k5b5tt23)します。</span><span class="sxs-lookup"><span data-stu-id="04e78-107">Try signing the assembly manually, using either the [Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) or the [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span></span>  
  
3.  <span data-ttu-id="04e78-108">エラーが続く場合は、状況に関する情報を収集し、マイクロソフト プロダクト サポート サービスに通知してください。</span><span class="sxs-lookup"><span data-stu-id="04e78-108">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-sign-the-assembly-manually"></a><span data-ttu-id="04e78-109">アセンブリを手動で署名するには</span><span class="sxs-lookup"><span data-stu-id="04e78-109">To sign the assembly manually</span></span>  
  
1.  <span data-ttu-id="04e78-110">使用して、 [Sn.exe (厳密名ツール)](https://msdn.microsoft.com/library/k5b5tt23)公開/秘密キー ペア ファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="04e78-110">Use the [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23) to create a public/private key pair file.</span></span>  
  
     <span data-ttu-id="04e78-111">このファイルは .snk の拡張子を持ちます。</span><span class="sxs-lookup"><span data-stu-id="04e78-111">This file has a .snk extension.</span></span>  
  
2.  <span data-ttu-id="04e78-112">エラーが発生している COM 参照をプロジェクトから削除します。</span><span class="sxs-lookup"><span data-stu-id="04e78-112">Delete the COM reference that is generating the error from your project.</span></span>  
  
3.  <span data-ttu-id="04e78-113">Windows の**開始** メニューをポイント**プログラム**、 をポイント**Microsoft Visual Studio 2008**、 をポイント**Visual Studio Tools**、 をクリックし、 **Visual Studio 2008 コマンド プロンプト**します。</span><span class="sxs-lookup"><span data-stu-id="04e78-113">From the Windows **Start** menu, point to **Programs**, point to **Microsoft Visual Studio 2008**, point to **Visual Studio Tools**, and then click **Visual Studio 2008 Command Prompt**.</span></span>  
  
4.  <span data-ttu-id="04e78-114">アセンブリ ラッパーを格納するディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="04e78-114">Move to the directory where you want to place your assembly wrapper.</span></span>  
  
5.  <span data-ttu-id="04e78-115">次のコードを入力します。</span><span class="sxs-lookup"><span data-stu-id="04e78-115">Type the following code.</span></span>  
  
    ```  
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>  
    ```  
  
     <span data-ttu-id="04e78-116">コードの一例として、次のように入力することができます。</span><span class="sxs-lookup"><span data-stu-id="04e78-116">An example of the code you might enter would be the following.</span></span>  
  
    ```  
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"  
    ```  
  
     <span data-ttu-id="04e78-117">パスやファイルに空白が含まれている場合には、二重引用符 (") を使用します。</span><span class="sxs-lookup"><span data-stu-id="04e78-117">Use double quotation marks (") if a path or file contains spaces.</span></span>  
  
6.  <span data-ttu-id="04e78-118">[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] で、作成したファイルに .NET アセンブリへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="04e78-118">In [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], add a .NET Assembly reference to the file you just created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04e78-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="04e78-119">See Also</span></span>  
 <span data-ttu-id="04e78-120">[Al.exe (アセンブリ リンカー)](https://msdn.microsoft.com/library/c405shex) </span><span class="sxs-lookup"><span data-stu-id="04e78-120">[Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) </span></span>  
<span data-ttu-id="04e78-121"> [Al.exe ツールのエラーと警告](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) </span><span class="sxs-lookup"><span data-stu-id="04e78-121"> [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) </span></span>  
<span data-ttu-id="04e78-122"> [Sn.exe (厳密名ツール)](https://msdn.microsoft.com/library/k5b5tt23) </span><span class="sxs-lookup"><span data-stu-id="04e78-122"> [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23) </span></span>  
<span data-ttu-id="04e78-123"> [方法 : 公開キーと秘密キーのキー ペアを作成する](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114) </span><span class="sxs-lookup"><span data-stu-id="04e78-123"> [How to: Create a Public-Private Key Pair](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114) </span></span>  
<span data-ttu-id="04e78-124"> [ご意見](https://docs.microsoft.com/visualstudio/ide/talk-to-us)</span><span class="sxs-lookup"><span data-stu-id="04e78-124"> [Talk to Us](https://docs.microsoft.com/visualstudio/ide/talk-to-us)</span></span>
