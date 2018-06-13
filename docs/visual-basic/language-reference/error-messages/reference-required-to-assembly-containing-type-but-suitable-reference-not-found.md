---
title: アセンブリに必要な参照&#39; &lt;assemblyidentity&gt; &#39;型を含む&#39; &lt;typename&gt;&#39;との間のあいまいなので、適切な参照が見つかりませんでしたが、プロジェクト&#39; &lt;projectname1&gt; &#39;と&#39; &lt;projectname2&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
ms.openlocfilehash: 670ac3ceb6a703a11b8f00a341dbcf868d4ceb7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597446"
---
# <a name="reference-required-to-assembly-39ltassemblyidentitygt39-containing-type-39lttypenamegt39-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-39ltprojectname1gt39-and-39ltprojectname2gt39"></a><span data-ttu-id="c87f5-102">アセンブリに必要な参照&#39; &lt;assemblyidentity&gt; &#39;型を含む&#39; &lt;typename&gt;&#39;との間のあいまいなので、適切な参照が見つかりませんでしたが、プロジェクト&#39; &lt;projectname1&gt; &#39;と&#39; &lt;projectname2&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="c87f5-102">Reference required to assembly &#39;&lt;assemblyidentity&gt;&#39; containing type &#39;&lt;typename&gt;&#39;, but a suitable reference could not be found due to ambiguity between projects &#39;&lt;projectname1&gt;&#39; and &#39;&lt;projectname2&gt;&#39;</span></span>
<span data-ttu-id="c87f5-103">プロジェクト外で定義されているクラス、構造体、インターフェイス、列挙型、デリゲートなどの型が式で使用されています。</span><span class="sxs-lookup"><span data-stu-id="c87f5-103">An expression uses a type, such as a class, structure, interface, enumeration, or delegate, that is defined outside your project.</span></span> <span data-ttu-id="c87f5-104">しかし、その型を定義する複数のアセンブリへのプロジェクト参照があります。</span><span class="sxs-lookup"><span data-stu-id="c87f5-104">However, you have project references to more than one assembly defining that type.</span></span>  
  
 <span data-ttu-id="c87f5-105">問題のプロジェクトは、同じ名前のアセンブリを複数作成します。</span><span class="sxs-lookup"><span data-stu-id="c87f5-105">The cited projects produce assemblies with the same name.</span></span> <span data-ttu-id="c87f5-106">このため、コンパイラは、アクセスしている型にどちらのアセンブリを使用すればよいかを判断できません。</span><span class="sxs-lookup"><span data-stu-id="c87f5-106">Therefore, the compiler cannot determine which assembly to use for the type you are accessing.</span></span>  
  
 <span data-ttu-id="c87f5-107">別のアセンブリで定義された型にアクセスするには、そのアセンブリへの参照が、Visual Basic コンパイラに必要です。</span><span class="sxs-lookup"><span data-stu-id="c87f5-107">To access a type defined in another assembly, the Visual Basic compiler must have a reference to that assembly.</span></span> <span data-ttu-id="c87f5-108">これは、プロジェクト間の循環参照にならない、単一であいまいさのない参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="c87f5-108">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="c87f5-109">**エラー ID:** BC30969</span><span class="sxs-lookup"><span data-stu-id="c87f5-109">**Error ID:** BC30969</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c87f5-110">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="c87f5-110">To correct this error</span></span>  
  
1.  <span data-ttu-id="c87f5-111">どのプロジェクトが、プロジェクトからの参照に最適なアセンブリを作成しているか特定します。</span><span class="sxs-lookup"><span data-stu-id="c87f5-111">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="c87f5-112">この判断には、ファイル アクセスの容易さや更新の頻度などの基準を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c87f5-112">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2.  <span data-ttu-id="c87f5-113">プロジェクトのプロパティに、使用する型が定義されているアセンブリを含むファイルへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="c87f5-113">In your project properties, add a reference to the file that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c87f5-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="c87f5-114">See Also</span></span>  
 [<span data-ttu-id="c87f5-115">プロジェクト内の参照の管理</span><span class="sxs-lookup"><span data-stu-id="c87f5-115">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 [<span data-ttu-id="c87f5-116">宣言された要素の参照</span><span class="sxs-lookup"><span data-stu-id="c87f5-116">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
   
 [<span data-ttu-id="c87f5-117">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="c87f5-117">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="c87f5-118">壊れた参照のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="c87f5-118">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
