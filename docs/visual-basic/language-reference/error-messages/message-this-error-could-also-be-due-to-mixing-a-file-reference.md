---
title: "&lt;メッセージ&gt;あるファイル参照アセンブリへのプロジェクト参照とを混在させる場合もこのエラー &quot;&lt;assemblyname&gt;&quot; |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30971
- vbc30971
dev_langs:
- VB
helpviewer_keywords:
- BC30971
ms.assetid: 75d2e8b5-2fdc-4623-8b32-cba805dab7db
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c0908b1a13b9b9c54fb533201404987e479c6138
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="ltmessagegt-this-error-could-also-be-due-to-mixing-a-file-reference-with-a-project-reference-to-assembly-39ltassemblynamegt39"></a><span data-ttu-id="21532-102">&lt;メッセージ&gt;あるファイル参照アセンブリへのプロジェクト参照とを混在させる場合もこのエラー '&lt;assemblyname&gt;'</span><span class="sxs-lookup"><span data-stu-id="21532-102">&lt;message&gt; This error could also be due to mixing a file reference with a project reference to assembly &#39;&lt;assemblyname&gt;&#39;</span></span>
<span data-ttu-id="21532-103">\<メッセージ > あるファイル参照アセンブリへのプロジェクト参照とを混在させる場合もこのエラー '\<assemblyname > します。</span><span class="sxs-lookup"><span data-stu-id="21532-103">\<message> This error could also be due to mixing a file reference with a project reference to assembly '\<assemblyname>.</span></span> <span data-ttu-id="21532-104">この場合、交換してみますファイル参照を '\<assemblyfilename >' プロジェクトで'\<projectname1 >' への参照をプロジェクトに '\<projectname2 >' です。</span><span class="sxs-lookup"><span data-stu-id="21532-104">In this case, try replacing the file reference to '\<assemblyfilename>' in project '\<projectname1>' with a project reference to '\<projectname2>'.</span></span>  
  
 <span data-ttu-id="21532-105">プロジェクト内のコードにアクセスする別のプロジェクトのメンバーが、ソリューションの構成が許可されていません、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラ、参照を解決します。</span><span class="sxs-lookup"><span data-stu-id="21532-105">Code in your project accesses a member of another project, but the configuration of your solution does not allow the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler to resolve the reference.</span></span>  
  
 <span data-ttu-id="21532-106">別のアセンブリで定義されている型にアクセスする、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラがそのアセンブリへの参照がある必要があります。</span><span class="sxs-lookup"><span data-stu-id="21532-106">To access a type defined in another assembly, the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler must have a reference to that assembly.</span></span> <span data-ttu-id="21532-107">これは、プロジェクト間の循環参照にならない、単一であいまいさのない参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="21532-107">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="21532-108">**エラー ID:** BC30971</span><span class="sxs-lookup"><span data-stu-id="21532-108">**Error ID:** BC30971</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="21532-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="21532-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="21532-110">どのプロジェクトが、プロジェクトからの参照に最適なアセンブリを作成しているか特定します。</span><span class="sxs-lookup"><span data-stu-id="21532-110">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="21532-111">この判断には、ファイル アクセスの容易さや更新の頻度などの基準を使用できます。</span><span class="sxs-lookup"><span data-stu-id="21532-111">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2.  <span data-ttu-id="21532-112">プロジェクトのプロパティに、使用する型が定義されているアセンブリを含むプロジェクトへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="21532-112">In your project properties, add a reference to the project that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21532-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="21532-113">See Also</span></span>  
 <span data-ttu-id="21532-114">[プロジェクトの参照を管理します。](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project) </span><span class="sxs-lookup"><span data-stu-id="21532-114">[Managing references in a project](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project) </span></span>  
<span data-ttu-id="21532-115"> [宣言された要素への参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md) </span><span class="sxs-lookup"><span data-stu-id="21532-115"> [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md) </span></span>  
<span data-ttu-id="21532-116"> [NIB 方法: [参照の追加] ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) </span><span class="sxs-lookup"><span data-stu-id="21532-116"> [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) </span></span>  
<span data-ttu-id="21532-117"> [NIB 方法: プロジェクトのプロパティと構成設定の変更](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67) </span><span class="sxs-lookup"><span data-stu-id="21532-117"> [NIB How to: Modify Project Properties and Configuration Settings](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67) </span></span>  
<span data-ttu-id="21532-118"> [壊れた参照のトラブルシューティング](https://docs.microsoft.com/visualstudio/ide/troubleshooting-broken-references)</span><span class="sxs-lookup"><span data-stu-id="21532-118"> [Troubleshooting Broken References](https://docs.microsoft.com/visualstudio/ide/troubleshooting-broken-references)</span></span>
