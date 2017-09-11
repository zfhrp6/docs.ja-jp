---
title: "#<a name=\"pragma-checksum-c-reference\"></a>#pragma checksum (C# リファレンス)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#pragma checksum'
dev_langs:
- CSharp
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
caps.latest.revision: 11
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c48d99843b9ba398dfe8dc3cf0d2264aaf72be9f
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="pragma-checksum-c-reference"></a><span data-ttu-id="f45bb-102">#pragma checksum (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="f45bb-102">#pragma checksum (C# Reference)</span></span>
<span data-ttu-id="f45bb-103">[!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] ページのデバッグに使用するソース ファイルのチェックサムを生成します。</span><span class="sxs-lookup"><span data-stu-id="f45bb-103">Generates checksums for source files to aid with debugging [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] pages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f45bb-104">構文</span><span class="sxs-lookup"><span data-stu-id="f45bb-104">Syntax</span></span>  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f45bb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f45bb-105">Parameters</span></span>  
 `"filename"`  
 <span data-ttu-id="f45bb-106">変更または更新を監視する必要があるファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="f45bb-106">The name of the file that requires monitoring for changes or updates.</span></span>  
  
 `"{guid}"`  
 <span data-ttu-id="f45bb-107">ファイルのグローバル一意識別子 (GUID)。</span><span class="sxs-lookup"><span data-stu-id="f45bb-107">The Globally Unique Identifier (GUID) for the file.</span></span>  
  
 `"checksum_bytes"`  
 <span data-ttu-id="f45bb-108">チェックサムのバイト数を表す 16 進数の文字列。</span><span class="sxs-lookup"><span data-stu-id="f45bb-108">The string of hexadecimal digits representing the bytes of the checksum.</span></span> <span data-ttu-id="f45bb-109">偶数の 16 進数である必要があります。</span><span class="sxs-lookup"><span data-stu-id="f45bb-109">Must be an even number of hexadecimal digits.</span></span> <span data-ttu-id="f45bb-110">奇数の数値を指定すると、コンパイル時に警告が出力され、ディレクティブが無視されます。</span><span class="sxs-lookup"><span data-stu-id="f45bb-110">An odd number of digits results in a compile-time warning, and the directive are  ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f45bb-111">コメント</span><span class="sxs-lookup"><span data-stu-id="f45bb-111">Remarks</span></span>  
 <span data-ttu-id="f45bb-112">Visual Studio デバッガーは、常に正しいソースを検出するために、チェックサムを使用します。</span><span class="sxs-lookup"><span data-stu-id="f45bb-112">The Visual Studio debugger uses a checksum to make sure  that it always finds the right source.</span></span> <span data-ttu-id="f45bb-113">コンパイラはソース ファイルのチェックサムを計算し、プログラム データベース (PDB) ファイルに結果を出力します。</span><span class="sxs-lookup"><span data-stu-id="f45bb-113">The compiler computes the checksum for a source file, and then emits the output to the program database (PDB) file.</span></span> <span data-ttu-id="f45bb-114">デバッガーは、その PDB ファイルを使用して、ソース ファイルについて計算したチェックサムと比較します。</span><span class="sxs-lookup"><span data-stu-id="f45bb-114">The debugger then uses the PDB to compare against the checksum that it computes for the source file.</span></span>  
  
 <span data-ttu-id="f45bb-115">このソリューションは [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] プロジェクトには使用できません。それは計算されたチェックサムは、.aspx ファイルではなく、生成されたソース ファイルを対象としているためです。</span><span class="sxs-lookup"><span data-stu-id="f45bb-115">This solution does not work for [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] projects, because the computed checksum is for the generated source file, rather than the .aspx file.</span></span> <span data-ttu-id="f45bb-116">この問題に対応するため、`#pragma checksum` によって [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] ページのチェックサムがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="f45bb-116">To address this problem, `#pragma checksum` provides checksum support for [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] pages.</span></span>  
  
 <span data-ttu-id="f45bb-117">[!INCLUDE[csprcs](~/includes/csprcs-md.md)] で [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] プロジェクトを作成すると、生成されるソース ファイルにソースの生成元である .aspx ファイルのチェックサムが含められます。</span><span class="sxs-lookup"><span data-stu-id="f45bb-117">When you create an [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] project in [!INCLUDE[csprcs](~/includes/csprcs-md.md)], the generated source file contains a checksum for the .aspx file, from which the source is generated.</span></span> <span data-ttu-id="f45bb-118">コンパイラは、この情報を PDB ファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="f45bb-118">The compiler then writes this information into the PDB file.</span></span>  
  
 <span data-ttu-id="f45bb-119">ファイルに `#pragma checksum` ディレクティブが見つからない場合、コンパイラはチェックサムを計算し、PDB ファイルにその値を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="f45bb-119">If the compiler encounters no `#pragma checksum` directive in the file, it computes the checksum and writes the value to the PDB file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f45bb-120">例</span><span class="sxs-lookup"><span data-stu-id="f45bb-120">Example</span></span>  
  
```csharp
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{3673e4ca-6098-4ec1-890f-8fceb2a794a2}" "{012345678AB}" // New checksum  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="f45bb-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="f45bb-121">See Also</span></span>  
 <span data-ttu-id="f45bb-122">[C# リファレンス](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="f45bb-122">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="f45bb-123">[C# プログラミング ガイド](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f45bb-123">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="f45bb-124">C# プリプロセッサ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="f45bb-124">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)

