---
title: 型の値&#39; &lt;typename1&gt; &#39;に変換できない&#39; &lt;typename2&gt; &#39; (複数のファイル参照)
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 41c18160be9b546f8b525376fa06bc0eca6c117a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39-multiple-file-references"></a><span data-ttu-id="28093-102">型の値&#39; &lt;typename1&gt; &#39;に変換できない&#39; &lt;typename2&gt; &#39; (複数のファイル参照)</span><span class="sxs-lookup"><span data-stu-id="28093-102">Value of type &#39;&lt;typename1&gt;&#39; cannot be converted to &#39;&lt;typename2&gt;&#39; (Multiple file references)</span></span>
<span data-ttu-id="28093-103">型の値 '\<typename1 >' に変換できません。'\<typename2 >' です。</span><span class="sxs-lookup"><span data-stu-id="28093-103">Value of type '\<typename1>' cannot be converted to '\<typename2>'.</span></span> <span data-ttu-id="28093-104">型の不一致へのファイル参照を混在させる可能性があります '\<filepath1 >' プロジェクトで'\<projectname1 >' へのファイル参照を '\<filepath2 >' プロジェクトで'\<projectname2 >' です。</span><span class="sxs-lookup"><span data-stu-id="28093-104">Type mismatch could be due to mixing a file reference to '\<filepath1>' in project '\<projectname1>' with a file reference to '\<filepath2>' in project '\<projectname2>'.</span></span> <span data-ttu-id="28093-105">両方のアセンブリが同一である場合は、これらの参照を同じ場所から参照するように置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="28093-105">If both assemblies are identical, try replacing these references so both references are from the same location.</span></span>  
  
 <span data-ttu-id="28093-106">状況では、プロジェクトは、1 つ以上のファイル参照アセンブリをコンパイラは、1 つの型を別に変換できることを保証できません。</span><span class="sxs-lookup"><span data-stu-id="28093-106">In a situation where a project makes more than one file reference to an assembly, the compiler cannot guarantee that one type can be converted to another.</span></span>  
  
 <span data-ttu-id="28093-107">それぞれのファイル参照は、ファイルのパスと (通常は DLL ファイル) のプロジェクトの出力ファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="28093-107">Each file reference specifies a file path and name for the output file of a project (typically a DLL file).</span></span> <span data-ttu-id="28093-108">コンパイラは、出力ファイルが、同じソースから取得することや、同じアセンブリの同じバージョンを表すことを保証できません。</span><span class="sxs-lookup"><span data-stu-id="28093-108">The compiler cannot guarantee that the output files come from the same source, or that they represent the same version of the same assembly.</span></span> <span data-ttu-id="28093-109">そのため、その種類別の参照では、同じの型またはも、あるは、その他に変換できることは保証できません。</span><span class="sxs-lookup"><span data-stu-id="28093-109">Therefore, it cannot guarantee that the types in the different references are the same type, or even that one can be converted to the other.</span></span>  
  
 <span data-ttu-id="28093-110">参照アセンブリが同じアセンブリ id を持つことがわかっている場合は、1 つのファイルの参照を使用できます。</span><span class="sxs-lookup"><span data-stu-id="28093-110">You can use a single file reference if you know that the referenced assemblies have the same assembly identity.</span></span> <span data-ttu-id="28093-111">*アセンブリ ID* には、アセンブリの名前、バージョン、公開キー (存在する場合)、およびカルチャが含まれます。</span><span class="sxs-lookup"><span data-stu-id="28093-111">The *assembly identity* includes the assembly's name, version, public key if any, and culture.</span></span> <span data-ttu-id="28093-112">この情報はアセンブリを一意に識別します。</span><span class="sxs-lookup"><span data-stu-id="28093-112">This information uniquely identifies the assembly.</span></span>  
  
 <span data-ttu-id="28093-113">**エラー ID:** BC30961</span><span class="sxs-lookup"><span data-stu-id="28093-113">**Error ID:** BC30961</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="28093-114">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="28093-114">To correct this error</span></span>  
  
-   <span data-ttu-id="28093-115">参照されるアセンブリのアセンブリ id が同じ場合は、削除するか、1 つのファイル参照のみがあるように、ファイル参照のいずれかを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="28093-115">If the referenced assemblies have the same assembly identity, then remove or replace one of the file references so that there is only a single file reference.</span></span>  
  
-   <span data-ttu-id="28093-116">参照アセンブリが同じアセンブリ id を持たない場合は、1 つのもう一方の型に型変換を行いませんようにコードを変更します。</span><span class="sxs-lookup"><span data-stu-id="28093-116">If the referenced assemblies do not have the same assembly identity, then change your code so that it does not attempt to convert a type in one to a type in the other.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28093-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="28093-117">See Also</span></span>  
 [<span data-ttu-id="28093-118">Visual Basic での型変換</span><span class="sxs-lookup"><span data-stu-id="28093-118">Type Conversions in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="28093-119">プロジェクト内の参照の管理</span><span class="sxs-lookup"><span data-stu-id="28093-119">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 
