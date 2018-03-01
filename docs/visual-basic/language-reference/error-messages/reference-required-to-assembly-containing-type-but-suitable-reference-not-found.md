---
title: "参照アセンブリ &#39; が必要です。&lt;assemblyidentity&gt;&#39;以外の場合は親の種類 &#39;&lt;typename&gt;&#39;以外の場合は、プロジェクト &#39; の間のあいまいなので、適切な参照が見つかりませんでしたが、&lt;projectname1&gt;&#39; と &#39;&lt;projectname2&gt;&#39;です。"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30969
- vbc30969
helpviewer_keywords:
- BC30969
ms.assetid: 1b29dbc5-8268-45fe-bfc2-b2070a5c845c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5ca2454f5c306b3defd1c885dfd59ee130f3e828
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="reference-required-to-assembly-39ltassemblyidentitygt39-containing-type-39lttypenamegt39-but-a-suitable-reference-could-not-be-found-due-to-ambiguity-between-projects-39ltprojectname1gt39-and-39ltprojectname2gt39"></a><span data-ttu-id="358dc-102">参照アセンブリ &#39; が必要です。&lt;assemblyidentity&gt;&#39;以外の場合は親の種類 &#39;&lt;typename&gt;&#39;以外の場合は、プロジェクト &#39; の間のあいまいなので、適切な参照が見つかりませんでしたが、&lt;projectname1&gt;&#39; と &#39;&lt;projectname2&gt;&#39;です。</span><span class="sxs-lookup"><span data-stu-id="358dc-102">Reference required to assembly &#39;&lt;assemblyidentity&gt;&#39; containing type &#39;&lt;typename&gt;&#39;, but a suitable reference could not be found due to ambiguity between projects &#39;&lt;projectname1&gt;&#39; and &#39;&lt;projectname2&gt;&#39;</span></span>
<span data-ttu-id="358dc-103">プロジェクト外で定義されているクラス、構造体、インターフェイス、列挙型、デリゲートなどの型が式で使用されています。</span><span class="sxs-lookup"><span data-stu-id="358dc-103">An expression uses a type, such as a class, structure, interface, enumeration, or delegate, that is defined outside your project.</span></span> <span data-ttu-id="358dc-104">しかし、その型を定義する複数のアセンブリへのプロジェクト参照があります。</span><span class="sxs-lookup"><span data-stu-id="358dc-104">However, you have project references to more than one assembly defining that type.</span></span>  
  
 <span data-ttu-id="358dc-105">問題のプロジェクトは、同じ名前のアセンブリを複数作成します。</span><span class="sxs-lookup"><span data-stu-id="358dc-105">The cited projects produce assemblies with the same name.</span></span> <span data-ttu-id="358dc-106">このため、コンパイラは、アクセスしている型にどちらのアセンブリを使用すればよいかを判断できません。</span><span class="sxs-lookup"><span data-stu-id="358dc-106">Therefore, the compiler cannot determine which assembly to use for the type you are accessing.</span></span>  
  
 <span data-ttu-id="358dc-107">別のアセンブリで定義されている型にアクセスするには、そのアセンブリへの参照を [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] コンパイラが保持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="358dc-107">To access a type defined in another assembly, the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler must have a reference to that assembly.</span></span> <span data-ttu-id="358dc-108">これは、プロジェクト間の循環参照にならない、単一であいまいさのない参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="358dc-108">This must be a single, unambiguous reference that does not cause circular references among projects.</span></span>  
  
 <span data-ttu-id="358dc-109">**エラー ID:** BC30969</span><span class="sxs-lookup"><span data-stu-id="358dc-109">**Error ID:** BC30969</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="358dc-110">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="358dc-110">To correct this error</span></span>  
  
1.  <span data-ttu-id="358dc-111">どのプロジェクトが、プロジェクトからの参照に最適なアセンブリを作成しているか特定します。</span><span class="sxs-lookup"><span data-stu-id="358dc-111">Determine which project produces the best assembly for your project to reference.</span></span> <span data-ttu-id="358dc-112">この判断には、ファイル アクセスの容易さや更新の頻度などの基準を使用できます。</span><span class="sxs-lookup"><span data-stu-id="358dc-112">For this decision, you might use criteria such as ease of file access and frequency of updates.</span></span>  
  
2.  <span data-ttu-id="358dc-113">プロジェクトのプロパティに、使用する型が定義されているアセンブリを含むファイルへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="358dc-113">In your project properties, add a reference to the file that contains the assembly that defines the type you are using.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="358dc-114">参照</span><span class="sxs-lookup"><span data-stu-id="358dc-114">See Also</span></span>  
 [<span data-ttu-id="358dc-115">プロジェクト内の参照の管理</span><span class="sxs-lookup"><span data-stu-id="358dc-115">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 [<span data-ttu-id="358dc-116">宣言された要素の参照</span><span class="sxs-lookup"><span data-stu-id="358dc-116">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
   
 [<span data-ttu-id="358dc-117">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="358dc-117">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="358dc-118">壊れた参照のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="358dc-118">Troubleshooting Broken References</span></span>](/visualstudio/ide/troubleshooting-broken-references)
