---
title: "&lt;メッセージ&gt;このエラーをファイル参照アセンブリ &#39; への参照をプロジェクトとの混合によって生じた可能性があります&lt;assemblyname&gt;&#39;です。"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30971
- vbc30971
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0fcbcc48928b1b03487f31930e3d14051ddd990a
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="ltmessagegt-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-39ltassemblynamegt39"></a><span data-ttu-id="32a55-102">&lt;メッセージ&gt;このエラーをファイル参照アセンブリ &#39; への参照をプロジェクトとの混合によって生じた可能性があります&lt;assemblyname&gt;&#39;です。</span><span class="sxs-lookup"><span data-stu-id="32a55-102">&lt;message&gt; This error could also be due to mixing a file reference with a project reference to assembly &#39;&lt;assemblyname&gt;&#39;</span></span>
<span data-ttu-id="32a55-103">\<メッセージ > このエラーをファイル参照アセンブリへの参照をプロジェクトとの混合によって生じた可能性があります '\<assemblyname >。</span><span class="sxs-lookup"><span data-stu-id="32a55-103">\<message> This error could also be due to mixing a file reference with a project reference to assembly '\<assemblyname>.</span></span> <span data-ttu-id="32a55-104">この場合、交換してみますファイル参照を '\<assemblyfilename >' プロジェクトで'\<projectname1 >' への参照をプロジェクトに '\<projectname2 >' です。</span><span class="sxs-lookup"><span data-stu-id="32a55-104">In this case, try replacing the file reference to '\<assemblyfilename>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>  
  
 <span data-ttu-id="32a55-105">プロジェクト内のコードが別のプロジェクトのメンバーにアクセスしていますが、このプロジェクトのソリューションは [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] コンパイラに参照の解決を許可するよう構成されていません。</span><span class="sxs-lookup"><span data-stu-id="32a55-105">Code in your project accesses a member of another project, but the configuration of your solution does not allow the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler to resolve the reference.</span></span>  
  
 <span data-ttu-id="32a55-106">別のアセンブリで定義されている型にアクセスするには、そのアセンブリへの参照を [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] コンパイラが保持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="32a55-106">To access a type defined in another assembly, the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler must have a reference to that assembly.</span></span> <span data-ttu-id="32a55-107">これは、プロジェクト間の循環参照にならない、単一であいまいさのない参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="32a55-107">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="32a55-108">**エラー ID:** BC30971</span><span class="sxs-lookup"><span data-stu-id="32a55-108">**Error ID:** BC30971</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="32a55-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="32a55-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="32a55-110">どのプロジェクトが、プロジェクトからの参照に最適なアセンブリを作成しているか特定します。</span><span class="sxs-lookup"><span data-stu-id="32a55-110">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="32a55-111">この判断には、ファイル アクセスの容易さや更新の頻度などの基準を使用できます。</span><span class="sxs-lookup"><span data-stu-id="32a55-111">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2.  <span data-ttu-id="32a55-112">プロジェクトのプロパティに、使用する型が定義されているアセンブリを含むプロジェクトへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="32a55-112">In your project properties, add a reference to the project that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32a55-113">参照</span><span class="sxs-lookup"><span data-stu-id="32a55-113">See Also</span></span>  
 [<span data-ttu-id="32a55-114">プロジェクト内の参照の管理</span><span class="sxs-lookup"><span data-stu-id="32a55-114">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 [<span data-ttu-id="32a55-115">宣言された要素の参照</span><span class="sxs-lookup"><span data-stu-id="32a55-115">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
   
 [<span data-ttu-id="32a55-116">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="32a55-116">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="32a55-117">壊れた参照のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="32a55-117">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
