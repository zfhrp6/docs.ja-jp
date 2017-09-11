---
title: "型の値 &quot;&lt;&quot; typename1 &quot;&gt;&quot;に変換できない&quot;&lt;typename2&gt;&quot; (複数のファイル参照) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30961
- bc30961
dev_langs:
- VB
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
caps.latest.revision: 9
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
ms.openlocfilehash: 299cc4bec00a4597a661c5da49135fe3b5357537
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39-multiple-file-references"></a><span data-ttu-id="8ddc4-102">型の値 '&lt;' typename1 '&gt;'に変換できない'&lt;typename2&gt;' (複数のファイル参照)</span><span class="sxs-lookup"><span data-stu-id="8ddc4-102">Value of type &#39;&lt;typename1&gt;&#39; cannot be converted to &#39;&lt;typename2&gt;&#39; (Multiple file references)</span></span>
<span data-ttu-id="8ddc4-103">型の値 '\<' typename1 '>' に変換できません。'\<typename2 >' です。</span><span class="sxs-lookup"><span data-stu-id="8ddc4-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="8ddc4-104">型の不一致に対するファイル参照の混在が考えられます '\<filepath1 >' プロジェクトで'\<projectname1 >' への参照をファイルに '\<filepath2 >' プロジェクトで'\<projectname2 >' です。</span><span class="sxs-lookup"><span data-stu-id="8ddc4-104">Type mismatch could be due to mixing a file reference to '\<filepath1>' in project '\<projectname1>' with a file reference to '\<filepath2>' in project '\<projectname2>'.</span></span> <span data-ttu-id="8ddc4-105">両方のアセンブリが同一である場合は、これらの参照を同じ場所から参照するように置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="8ddc4-105">If both assemblies are identical, try replacing these references so both references are from the same location.</span></span>  
  
 <span data-ttu-id="8ddc4-106">プロジェクトはアセンブリへの&1; つ以上のファイル参照を状況の場合、コンパイラは、別に、1 つの型を変換できることを保証できません。</span><span class="sxs-lookup"><span data-stu-id="8ddc4-106">In a situation where a project makes more than one file reference to an assembly, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="8ddc4-107">それぞれのファイル参照は、ファイルのパスとプロジェクト (通常は DLL ファイル) の出力ファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="8ddc4-107">Each file reference specifies a file path and name for the output file of a project (typically a DLL file).</span></span> <span data-ttu-id="8ddc4-108">コンパイラは、出力ファイルが同じソースから取得するか、同じアセンブリの同じバージョンを表すことを保証できません。</span><span class="sxs-lookup"><span data-stu-id="8ddc4-108">The compiler cannot guarantee that the output files come from the same source, or that they represent the same version of the same assembly.</span></span> <span data-ttu-id="8ddc4-109">したがって、種類別の参照では、同じ型か、その他にも、あるを変換できることを保証することはできません。</span><span class="sxs-lookup"><span data-stu-id="8ddc4-109">Therefore, it cannot guarantee that the types in the different references are the same type, or even that one can be converted to the other.</span></span>  
  
 <span data-ttu-id="8ddc4-110">参照先アセンブリのアセンブリ id が同じであることがわかっている場合は、1 つのファイルの参照を使用できます。</span><span class="sxs-lookup"><span data-stu-id="8ddc4-110">You can use a single file reference if you know that the referenced assemblies have the same assembly identity.</span></span> <span data-ttu-id="8ddc4-111">*アセンブリ ID* には、アセンブリの名前、バージョン、公開キー (存在する場合)、およびカルチャが含まれます。</span><span class="sxs-lookup"><span data-stu-id="8ddc4-111">The *assembly identity* includes the assembly's name, version, public key if any, and culture.</span></span> <span data-ttu-id="8ddc4-112">この情報はアセンブリを一意に識別します。</span><span class="sxs-lookup"><span data-stu-id="8ddc4-112">This information uniquely identifies the assembly.</span></span>  
  
 <span data-ttu-id="8ddc4-113">**エラー ID:** BC30961</span><span class="sxs-lookup"><span data-stu-id="8ddc4-113">**Error ID:** BC30961</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8ddc4-114">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="8ddc4-114">To correct this error</span></span>  
  
-   <span data-ttu-id="8ddc4-115">参照先アセンブリのアセンブリ id が同じ場合は、削除や、置き換えるファイルの参照のいずれか&1; つのファイル参照のみがあります。</span><span class="sxs-lookup"><span data-stu-id="8ddc4-115">If the referenced assemblies have the same assembly identity, then remove or replace one of the file references so that there is only a single file reference.</span></span>  
  
-   <span data-ttu-id="8ddc4-116">参照されたアセンブリは同じアセンブリの id を持っていない場合は、1 つのもう一方の型に型変換を行いませんようにコードを変更します。</span><span class="sxs-lookup"><span data-stu-id="8ddc4-116">If the referenced assemblies do not have the same assembly identity, then change your code so that it does not attempt to convert a type in one to a type in the other.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ddc4-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="8ddc4-117">See Also</span></span>  
 <span data-ttu-id="8ddc4-118">[Visual Basic における型変換](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="8ddc4-118">[Type Conversions in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
<span data-ttu-id="8ddc4-119"> [プロジェクトの参照を管理します。](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project) </span><span class="sxs-lookup"><span data-stu-id="8ddc4-119"> [Managing references in a project](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project) </span></span>  
<span data-ttu-id="8ddc4-120"> [NIB 方法: [参照の追加] ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)</span><span class="sxs-lookup"><span data-stu-id="8ddc4-120"> [NIB How to: Add or Remove References By Using the Add Reference Dialog Box](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)</span></span>
