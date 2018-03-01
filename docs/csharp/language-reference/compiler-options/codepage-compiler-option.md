---
title: "-codepage (C# コンパイラ オプション)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c1181ef98ac5f335c9737771eda2b3bd9227cc9f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="-codepage-c-compiler-options"></a><span data-ttu-id="575ff-102">-codepage (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="575ff-102">-codepage (C# Compiler Options)</span></span>
<span data-ttu-id="575ff-103">このオプションでは、必要とするページが、システムで使用されている現在の既定のコードページでない場合に、コンパイル時に使用するコード ページを指定します。</span><span class="sxs-lookup"><span data-stu-id="575ff-103">This option specifies which codepage to use during compilation if the required page is not the current default codepage for the system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="575ff-104">構文</span><span class="sxs-lookup"><span data-stu-id="575ff-104">Syntax</span></span>  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="575ff-105">引数</span><span class="sxs-lookup"><span data-stu-id="575ff-105">Arguments</span></span>  
 `id`  
 <span data-ttu-id="575ff-106">コンパイル時にすべてのソース コード ファイルで使うコード ページの ID です。</span><span class="sxs-lookup"><span data-stu-id="575ff-106">The id of the code page to use for all source code files in the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="575ff-107">コメント</span><span class="sxs-lookup"><span data-stu-id="575ff-107">Remarks</span></span>  
 <span data-ttu-id="575ff-108">コンピューターの既定のコード ページを使わずに作成されたソース コード ファイルをコンパイルする場合は、**-codepage** オプションで、使用するコード ページを指定できます。</span><span class="sxs-lookup"><span data-stu-id="575ff-108">If you compile one or more source code files that were not created to use the default code page on your computer, you can use the **-codepage** option to specify which code page should be used.</span></span> <span data-ttu-id="575ff-109">**-codepage** は、コンパイル時にすべてのソース コード ファイルに適用されます。</span><span class="sxs-lookup"><span data-stu-id="575ff-109">**-codepage** applies to all source code files in your compilation.</span></span>  
  
 <span data-ttu-id="575ff-110">ソース コード ファイルが、コンピューターで有効なコード ページと同じものを使って作成された場合、または UNICODE か UTF-8 で作成された場合、**-codepage** を使う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="575ff-110">If the source code files were created with the same codepage that is in effect on your computer or if the source code files were created with UNICODE or UTF-8, you need not use **-codepage**.</span></span>  
  
 <span data-ttu-id="575ff-111">使用しているシステムでサポートされているコード ページを確認する方法については、[GetCPInfo](https://msdn.microsoft.com/library/dd318078(VS.85).aspx) に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="575ff-111">See [GetCPInfo](https://msdn.microsoft.com/library/dd318078(VS.85).aspx) for information on how to find which code pages are supported on your system.</span></span>  
  
 <span data-ttu-id="575ff-112">このコンパイラ オプションは Visual Studio では使用できず、プログラムで変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="575ff-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="575ff-113">参照</span><span class="sxs-lookup"><span data-stu-id="575ff-113">See Also</span></span>  
 [<span data-ttu-id="575ff-114">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="575ff-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="575ff-115">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="575ff-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
