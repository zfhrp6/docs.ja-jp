---
title: "/reference (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
caps.latest.revision: 16
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
ms.openlocfilehash: 6870c0b6008124bad18f8eba9207d06e085f2307
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="reference-visual-basic"></a><span data-ttu-id="2bf98-102">/reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2bf98-102">/reference (Visual Basic)</span></span>
<span data-ttu-id="2bf98-103">コンパイラで指定したアセンブリ内の型情報をプロジェクトのコンパイル中にできるようにします。</span><span class="sxs-lookup"><span data-stu-id="2bf98-103">Causes the compiler to make type information in the specified assemblies available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bf98-104">構文</span><span class="sxs-lookup"><span data-stu-id="2bf98-104">Syntax</span></span>  
  
```  
/reference:fileList  
' -or-  
/r:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="2bf98-105">引数</span><span class="sxs-lookup"><span data-stu-id="2bf98-105">Arguments</span></span>  
  
|<span data-ttu-id="2bf98-106">用語</span><span class="sxs-lookup"><span data-stu-id="2bf98-106">Term</span></span>|<span data-ttu-id="2bf98-107">定義</span><span class="sxs-lookup"><span data-stu-id="2bf98-107">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="2bf98-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="2bf98-108">Required.</span></span> <span data-ttu-id="2bf98-109">アセンブリ ファイル名のコンマ区切りリスト。</span><span class="sxs-lookup"><span data-stu-id="2bf98-109">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="2bf98-110">ファイル名にスペースが含まれている場合は、名前を引用符で囲みます。</span><span class="sxs-lookup"><span data-stu-id="2bf98-110">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2bf98-111">コメント</span><span class="sxs-lookup"><span data-stu-id="2bf98-111">Remarks</span></span>  
 <span data-ttu-id="2bf98-112">インポートするファイルは、アセンブリ メタデータを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="2bf98-112">The file(s) you import must contain assembly metadata.</span></span> <span data-ttu-id="2bf98-113">パブリック型だけでは、アセンブリの外側に表示されます。</span><span class="sxs-lookup"><span data-stu-id="2bf98-113">Only public types are visible outside the assembly.</span></span> <span data-ttu-id="2bf98-114">[/Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)オプションは、モジュールからメタデータをインポートします。</span><span class="sxs-lookup"><span data-stu-id="2bf98-114">The [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) option imports metadata from a module.</span></span>  
  
 <span data-ttu-id="2bf98-115">アセンブリ (アセンブリ A) を参照する場合は、別のアセンブリ (アセンブリ B) を参照する場合に、アセンブリ B を参照する必要は。</span><span class="sxs-lookup"><span data-stu-id="2bf98-115">If you reference an assembly (Assembly A) which itself references another assembly (Assembly B), you need to reference Assembly B if:</span></span>  
  
-   <span data-ttu-id="2bf98-116">アセンブリ A から型の型から継承またはアセンブリ B のインターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="2bf98-116">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="2bf98-117">フィールド、プロパティ、イベント、またはアセンブリ B の戻り値の型またはパラメーターの型を持つメソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="2bf98-117">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="2bf98-118">使用[/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)を&1; つ以上のアセンブリ参照があるディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="2bf98-118">Use [/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="2bf98-119">コンパイラがアセンブリ (モジュールではなく) の型を認識するには、型の解決を強制する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2bf98-119">For the compiler to recognize a type in an assembly (not a module), it must be forced to resolve the type.</span></span> <span data-ttu-id="2bf98-120">この操作方法の&1; つの例では、型のインスタンスを定義します。</span><span class="sxs-lookup"><span data-stu-id="2bf98-120">One example of how you can do this is to define an instance of the type.</span></span> <span data-ttu-id="2bf98-121">その他の方法は、コンパイラがアセンブリ内の型名を解決するには使用できます。</span><span class="sxs-lookup"><span data-stu-id="2bf98-121">Other ways are available to resolve type names in an assembly for the compiler.</span></span> <span data-ttu-id="2bf98-122">たとえば、アセンブリ内の型から継承する場合、型名し、既知となるコンパイラにします。</span><span class="sxs-lookup"><span data-stu-id="2bf98-122">For example, if you inherit from a type in an assembly, the type name then becomes known to the compiler.</span></span>  
  
 <span data-ttu-id="2bf98-123">参照は通常、使用、Vbc.rsp 応答ファイル[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]アセンブリが既定で使用します。</span><span class="sxs-lookup"><span data-stu-id="2bf98-123">The Vbc.rsp response file, which references commonly used [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblies, is used by default.</span></span> <span data-ttu-id="2bf98-124">使用して`/noconfig`Vbc.rsp を使うようコンパイラにしたくない場合。</span><span class="sxs-lookup"><span data-stu-id="2bf98-124">Use `/noconfig` if you do not want the compiler to use Vbc.rsp.</span></span>  
  
 <span data-ttu-id="2bf98-125">短い形式の`/reference`は`/r`です。</span><span class="sxs-lookup"><span data-stu-id="2bf98-125">The short form of `/reference` is `/r`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bf98-126">例</span><span class="sxs-lookup"><span data-stu-id="2bf98-126">Example</span></span>  
 <span data-ttu-id="2bf98-127">次のコードのコンパイルのソース ファイルは`nput.vb`M からアセンブリを参照および`etad1.dll`と M`etad2.dll` O を生成する`ut.exe`です。</span><span class="sxs-lookup"><span data-stu-id="2bf98-127">The following code compiles source file I`nput.vb` and reference assemblies from M`etad1.dll` and M`etad2.dll` to produce O`ut.exe`.</span></span>  
  
```  
vbc /reference:metad1.dll,metad2.dll /out:out.exe input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="2bf98-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="2bf98-128">See Also</span></span>  
 <span data-ttu-id="2bf98-129">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="2bf98-129">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="2bf98-130"> [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) </span><span class="sxs-lookup"><span data-stu-id="2bf98-130"> [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md) </span></span>  
<span data-ttu-id="2bf98-131"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span><span class="sxs-lookup"><span data-stu-id="2bf98-131"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span></span>  
<span data-ttu-id="2bf98-132"> [パブリック](../../../visual-basic/language-reference/modifiers/public.md) </span><span class="sxs-lookup"><span data-stu-id="2bf98-132"> [Public](../../../visual-basic/language-reference/modifiers/public.md) </span></span>  
<span data-ttu-id="2bf98-133"> [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="2bf98-133"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
