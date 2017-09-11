---
title: "/win32resource |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /win32resource
- win32resource
dev_langs:
- VB
helpviewer_keywords:
- /win32resource compiler option [Visual Basic]
- -win32resource compiler option [Visual Basic]
- win32resource compiler option [Visual Basic]
ms.assetid: e226946d-19ce-4cc9-91f5-aed24f77aa2b
caps.latest.revision: 13
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
ms.openlocfilehash: dc6bbb5948a5dd505f0fc4d1c8a86650214d657a
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="win32resource"></a><span data-ttu-id="7b62b-102">/win32resource</span><span class="sxs-lookup"><span data-stu-id="7b62b-102">/win32resource</span></span>
<span data-ttu-id="7b62b-103">出力ファイルには、Win32 リソース ファイルを挿入します。</span><span class="sxs-lookup"><span data-stu-id="7b62b-103">Inserts a Win32 resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b62b-104">構文</span><span class="sxs-lookup"><span data-stu-id="7b62b-104">Syntax</span></span>  
  
```  
/win32resource:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="7b62b-105">引数</span><span class="sxs-lookup"><span data-stu-id="7b62b-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="7b62b-106">出力ファイルに追加するリソース ファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="7b62b-106">The name of the resource file to add to your output file.</span></span> <span data-ttu-id="7b62b-107">ファイル名を引用符で囲みます ("")、スペースが含まれている場合。</span><span class="sxs-lookup"><span data-stu-id="7b62b-107">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b62b-108">コメント</span><span class="sxs-lookup"><span data-stu-id="7b62b-108">Remarks</span></span>  
 <span data-ttu-id="7b62b-109">Microsoft Windows リソース コンパイラ (RC) には、Win32 リソース ファイルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="7b62b-109">You can create a Win32 resource file with the Microsoft Windows Resource Compiler (RC).</span></span>  
  
 <span data-ttu-id="7b62b-110">Win32 リソースのバージョンを含めることができますかでアプリケーションを識別するために役立つビットマップ (アイコン) 情報**ファイル エクスプ ローラー**します。</span><span class="sxs-lookup"><span data-stu-id="7b62b-110">A Win32 resource can contain version or bitmap (icon) information that helps identify your application in **File Explorer**.</span></span> <span data-ttu-id="7b62b-111">指定しない場合`/win32resource`コンパイラはアセンブリのバージョンに基づくバージョン情報を生成します。</span><span class="sxs-lookup"><span data-stu-id="7b62b-111">If you do not specify `/win32resource`, the compiler generates version information based on the assembly version.</span></span> <span data-ttu-id="7b62b-112">`/win32resource`と`/win32icon`オプションは相互に排他的です。</span><span class="sxs-lookup"><span data-stu-id="7b62b-112">The `/win32resource` and `/win32icon` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="7b62b-113">参照してください[/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md)参照に、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]リソース ファイルまたは[/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md)をアタッチする、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]リソース ファイル。</span><span class="sxs-lookup"><span data-stu-id="7b62b-113">See [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] resource file, or [/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] resource file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7b62b-114">`/win32resource`オプションは、Visual Studio 開発環境内から使用できません。 コマンドラインからコンパイルする場合だけに利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="7b62b-114">The `/win32resource` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b62b-115">例</span><span class="sxs-lookup"><span data-stu-id="7b62b-115">Example</span></span>  
 <span data-ttu-id="7b62b-116">次のコードのコンパイル`In.vb`し、Win32 リソース ファイルを添付`Rf.res`:</span><span class="sxs-lookup"><span data-stu-id="7b62b-116">The following code compiles `In.vb` and attaches a Win32 resource file, `Rf.res`:</span></span>  
  
```  
vbc /win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="7b62b-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="7b62b-117">See Also</span></span>  
 <span data-ttu-id="7b62b-118">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="7b62b-118">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="7b62b-119"> [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="7b62b-119"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
