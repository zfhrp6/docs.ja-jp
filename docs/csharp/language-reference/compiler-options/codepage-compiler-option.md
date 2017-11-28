---
title: "-codepage (C# コンパイラ オプション)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 37f40312f1218b8e666eae7cb2de6c768ee32108
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="codepage-c-compiler-options"></a><span data-ttu-id="4f890-102">/codepage (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="4f890-102">/codepage (C# Compiler Options)</span></span>
<span data-ttu-id="4f890-103">このオプションでは、必要とするページが、システムで使用されている現在の既定のコードページでない場合に、コンパイル時に使用するコード ページを指定します。</span><span class="sxs-lookup"><span data-stu-id="4f890-103">This option specifies which codepage to use during compilation if the required page is not the current default codepage for the system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f890-104">構文</span><span class="sxs-lookup"><span data-stu-id="4f890-104">Syntax</span></span>  
  
```console  
/codepage:id  
```  
  
## <a name="arguments"></a><span data-ttu-id="4f890-105">引数</span><span class="sxs-lookup"><span data-stu-id="4f890-105">Arguments</span></span>  
 `id`  
 <span data-ttu-id="4f890-106">コンパイル時にすべてのソース コード ファイルで使うコード ページの ID です。</span><span class="sxs-lookup"><span data-stu-id="4f890-106">The id of the code page to use for all source code files in the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f890-107">コメント</span><span class="sxs-lookup"><span data-stu-id="4f890-107">Remarks</span></span>  
 <span data-ttu-id="4f890-108">コンピューターの既定のコード ページを使わずに作成されたソース コード ファイルをコンパイルする場合は、**/codepage** オプションで、使用するコード ページを指定できます。</span><span class="sxs-lookup"><span data-stu-id="4f890-108">If you compile one or more source code files that were not created to use the default code page on your computer, you can use the **/codepage** option to specify which code page should be used.</span></span> <span data-ttu-id="4f890-109">**/codepage** は、コンパイル時にすべてのソース コード ファイルに適用されます。</span><span class="sxs-lookup"><span data-stu-id="4f890-109">**/codepage** applies to all source code files in your compilation.</span></span>  
  
 <span data-ttu-id="4f890-110">ソース コード ファイルが、コンピューターで有効なコード ページと同じものを使って作成された場合、または UNICODE か UTF-8 で作成された場合、**/codepage** を使う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4f890-110">If the source code files were created with the same codepage that is in effect on your computer or if the source code files were created with UNICODE or UTF-8, you need not use **/codepage**.</span></span>  
  
 <span data-ttu-id="4f890-111">使用しているシステムでサポートされているコード ページを確認する方法については、[GetCPInfo](http://go.microsoft.com/fwlink/?LinkId=148371) に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4f890-111">See [GetCPInfo](http://go.microsoft.com/fwlink/?LinkId=148371) for information on how to find which code pages are supported on your system.</span></span>  
  
 <span data-ttu-id="4f890-112">このコンパイラ オプションは Visual Studio では使用できず、プログラムで変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="4f890-112">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f890-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f890-113">See Also</span></span>  
 [<span data-ttu-id="4f890-114">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="4f890-114">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="4f890-115">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="4f890-115">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
