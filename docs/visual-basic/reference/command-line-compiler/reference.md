---
title: /reference (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f8c6851802afa818cc80b3f6d7eafc2ef47ac689
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="reference-visual-basic"></a><span data-ttu-id="76d17-102">/reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76d17-102">/reference (Visual Basic)</span></span>
<span data-ttu-id="76d17-103">コンパイラで指定されたアセンブリ内の型情報をプロジェクトのコンパイル中にできるようにします。</span><span class="sxs-lookup"><span data-stu-id="76d17-103">Causes the compiler to make type information in the specified assemblies available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76d17-104">構文</span><span class="sxs-lookup"><span data-stu-id="76d17-104">Syntax</span></span>  
  
```  
/reference:fileList  
' -or-  
/r:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="76d17-105">引数</span><span class="sxs-lookup"><span data-stu-id="76d17-105">Arguments</span></span>  
  
|<span data-ttu-id="76d17-106">用語</span><span class="sxs-lookup"><span data-stu-id="76d17-106">Term</span></span>|<span data-ttu-id="76d17-107">定義</span><span class="sxs-lookup"><span data-stu-id="76d17-107">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="76d17-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="76d17-108">Required.</span></span> <span data-ttu-id="76d17-109">アセンブリ ファイル名のコンマ区切りリスト。</span><span class="sxs-lookup"><span data-stu-id="76d17-109">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="76d17-110">ファイル名に空白が含まれている場合は、名前を二重引用符で囲みます。</span><span class="sxs-lookup"><span data-stu-id="76d17-110">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76d17-111">コメント</span><span class="sxs-lookup"><span data-stu-id="76d17-111">Remarks</span></span>  
 <span data-ttu-id="76d17-112">インポートするファイルは、アセンブリ メタデータを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="76d17-112">The file(s) you import must contain assembly metadata.</span></span> <span data-ttu-id="76d17-113">パブリック型だけでは、アセンブリの外側に表示されます。</span><span class="sxs-lookup"><span data-stu-id="76d17-113">Only public types are visible outside the assembly.</span></span> <span data-ttu-id="76d17-114">[/Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)オプションは、モジュールからメタデータをインポートします。</span><span class="sxs-lookup"><span data-stu-id="76d17-114">The [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) option imports metadata from a module.</span></span>  
  
 <span data-ttu-id="76d17-115">アセンブリ (アセンブリ A) を参照する場合は、別のアセンブリ (アセンブリ B) を参照する、必要な参照アセンブリ B 場合。</span><span class="sxs-lookup"><span data-stu-id="76d17-115">If you reference an assembly (Assembly A) which itself references another assembly (Assembly B), you need to reference Assembly B if:</span></span>  
  
-   <span data-ttu-id="76d17-116">アセンブリ A の型がアセンブリ B の型から継承されているか、アセンブリ B のインターフェイスを実装する。</span><span class="sxs-lookup"><span data-stu-id="76d17-116">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="76d17-117">アセンブリ B の戻り値の型またはパラメーターの型を使用するフィールド、プロパティ、イベント、またはメソッドが呼び出される。</span><span class="sxs-lookup"><span data-stu-id="76d17-117">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="76d17-118">使用して[/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)を 1 つ以上のアセンブリ参照があるディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="76d17-118">Use [/libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="76d17-119">アセンブリ モジュールではなく) 内の型を認識するようにコンパイラで型の解決を強制する必要があります。</span><span class="sxs-lookup"><span data-stu-id="76d17-119">For the compiler to recognize a type in an assembly (not a module), it must be forced to resolve the type.</span></span> <span data-ttu-id="76d17-120">この操作方法の 1 つの例では、型のインスタンスを定義します。</span><span class="sxs-lookup"><span data-stu-id="76d17-120">One example of how you can do this is to define an instance of the type.</span></span> <span data-ttu-id="76d17-121">その他の方法は、コンパイラがアセンブリ内の型名を解決するには利用できます。</span><span class="sxs-lookup"><span data-stu-id="76d17-121">Other ways are available to resolve type names in an assembly for the compiler.</span></span> <span data-ttu-id="76d17-122">たとえば、アセンブリ内の型から継承する場合、型名し既知となるコンパイラにします。</span><span class="sxs-lookup"><span data-stu-id="76d17-122">For example, if you inherit from a type in an assembly, the type name then becomes known to the compiler.</span></span>  
  
 <span data-ttu-id="76d17-123">参照がよく使用される、Vbc.rsp 応答ファイル[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]アセンブリは既定で使用します。</span><span class="sxs-lookup"><span data-stu-id="76d17-123">The Vbc.rsp response file, which references commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies, is used by default.</span></span> <span data-ttu-id="76d17-124">使用して`/noconfig`コンパイラが Vbc.rsp を使用したくない場合。</span><span class="sxs-lookup"><span data-stu-id="76d17-124">Use `/noconfig` if you do not want the compiler to use Vbc.rsp.</span></span>  
  
 <span data-ttu-id="76d17-125">`/reference` の省略形は `/r` です。</span><span class="sxs-lookup"><span data-stu-id="76d17-125">The short form of `/reference` is `/r`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76d17-126">例</span><span class="sxs-lookup"><span data-stu-id="76d17-126">Example</span></span>  
 <span data-ttu-id="76d17-127">次のコードは、ソース ファイル `Input.vb` と、`Metad1.dll` および `Metad2.dll` からの参照アセンブリをコンパイルして、`Out.exe` を生成します。</span><span class="sxs-lookup"><span data-stu-id="76d17-127">The following code compiles source file `Input.vb` and reference assemblies from `Metad1.dll` and `Metad2.dll` to produce `Out.exe`.</span></span>  
  
```  
vbc /reference:metad1.dll,metad2.dll /out:out.exe input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="76d17-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="76d17-128">See Also</span></span>  
 [<span data-ttu-id="76d17-129">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="76d17-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="76d17-130">/noconfig</span><span class="sxs-lookup"><span data-stu-id="76d17-130">/noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [<span data-ttu-id="76d17-131">/target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="76d17-131">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="76d17-132">Public</span><span class="sxs-lookup"><span data-stu-id="76d17-132">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="76d17-133">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="76d17-133">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
