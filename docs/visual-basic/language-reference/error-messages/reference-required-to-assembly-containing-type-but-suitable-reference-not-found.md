---
title: "参照アセンブリが必要です &quot;&lt;assemblyidentity&gt;&quot;型を含む&quot;&lt;typename&gt;&quot;、プロジェクトの間のあいまいなので、適切な参照が見つかりませんでしたが、&lt;projectname1&gt;&quot;と&quot;&lt;projectname2&gt;&quot; |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30969
- vbc30969
dev_langs:
- VB
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
caps.latest.revision: 11
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
ms.openlocfilehash: bb5375366fa525a0ca9c16944d026ca499062ed8
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="reference-required-to-assembly-39ltassemblyidentitygt39-containing-type-39lttypenamegt39-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-39ltprojectname1gt39-and-39ltprojectname2gt39"></a><span data-ttu-id="70d1a-102">参照アセンブリが必要です '&lt;assemblyidentity&gt;'型を含む'&lt;typename&gt;'、プロジェクトの間のあいまいなので、適切な参照が見つかりませんでしたが、&lt;projectname1&gt;'と'&lt;projectname2&gt;'</span><span class="sxs-lookup"><span data-stu-id="70d1a-102">Reference required to assembly &#39;&lt;assemblyidentity&gt;&#39; containing type &#39;&lt;typename&gt;&#39;, but a suitable reference could not be found due to ambiguity between projects &#39;&lt;projectname1&gt;&#39; and &#39;&lt;projectname2&gt;&#39;</span></span>
<span data-ttu-id="70d1a-103">プロジェクト外で定義されているクラス、構造体、インターフェイス、列挙型、デリゲートなどの型が式で使用されています。</span><span class="sxs-lookup"><span data-stu-id="70d1a-103">An expression uses a type, such as a class, structure, interface, enumeration, or delegate, that is defined outside your project.</span></span> <span data-ttu-id="70d1a-104">しかし、その型を定義する複数のアセンブリへのプロジェクト参照があります。</span><span class="sxs-lookup"><span data-stu-id="70d1a-104">However, you have project references to more than one assembly defining that type.</span></span>  
  
 <span data-ttu-id="70d1a-105">問題のプロジェクトは、同じ名前のアセンブリを複数作成します。</span><span class="sxs-lookup"><span data-stu-id="70d1a-105">The cited projects produce assemblies with the same name.</span></span> <span data-ttu-id="70d1a-106">このため、コンパイラは、アクセスしている型にどちらのアセンブリを使用すればよいかを判断できません。</span><span class="sxs-lookup"><span data-stu-id="70d1a-106">Therefore, the compiler cannot determine which assembly to use for the type you are accessing.</span></span>  
  
 <span data-ttu-id="70d1a-107">別のアセンブリで定義されている型にアクセスする、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラがそのアセンブリへの参照がある必要があります。</span><span class="sxs-lookup"><span data-stu-id="70d1a-107">To access a type defined in another assembly, the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler must have a reference to that assembly.</span></span> <span data-ttu-id="70d1a-108">これは、プロジェクト間の循環参照にならない、単一であいまいさのない参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="70d1a-108">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="70d1a-109">**エラー ID:** BC30969</span><span class="sxs-lookup"><span data-stu-id="70d1a-109">**Error ID:** BC30969</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="70d1a-110">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="70d1a-110">To correct this error</span></span>  
  
1.  <span data-ttu-id="70d1a-111">どのプロジェクトが、プロジェクトからの参照に最適なアセンブリを作成しているか特定します。</span><span class="sxs-lookup"><span data-stu-id="70d1a-111">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="70d1a-112">この判断には、ファイル アクセスの容易さや更新の頻度などの基準を使用できます。</span><span class="sxs-lookup"><span data-stu-id="70d1a-112">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2.  <span data-ttu-id="70d1a-113">プロジェクトのプロパティに、使用する型が定義されているアセンブリを含むファイルへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="70d1a-113">In your project properties, add a reference to the file that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70d1a-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="70d1a-114">See Also</span></span>  
 <span data-ttu-id="70d1a-115">[プロジェクトの参照を管理します。](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project) </span><span class="sxs-lookup"><span data-stu-id="70d1a-115">[Managing references in a project](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project) </span></span>  
<span data-ttu-id="70d1a-116"> [宣言された要素への参照](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md) </span><span class="sxs-lookup"><span data-stu-id="70d1a-116"> [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md) </span></span>  
<span data-ttu-id="70d1a-117"> [NIB 方法: [参照の追加] ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) </span><span class="sxs-lookup"><span data-stu-id="70d1a-117"> [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) </span></span>  
<span data-ttu-id="70d1a-118"> [NIB 方法: プロジェクトのプロパティと構成設定の変更](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67) </span><span class="sxs-lookup"><span data-stu-id="70d1a-118"> [NIB How to: Modify Project Properties and Configuration Settings](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67) </span></span>  
<span data-ttu-id="70d1a-119"> [壊れた参照のトラブルシューティング](https://docs.microsoft.com/visualstudio/ide/troubleshooting-broken-references)</span><span class="sxs-lookup"><span data-stu-id="70d1a-119"> [Troubleshooting Broken References](https://docs.microsoft.com/visualstudio/ide/troubleshooting-broken-references)</span></span>
