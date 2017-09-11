---
title: "/errorreport |Microsoft ドキュメント"
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
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c2f9a9daf6aed6348baeb2c4de2fe5caef70f52b
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="errorreport"></a><span data-ttu-id="6ba39-102">/errorreport</span><span class="sxs-lookup"><span data-stu-id="6ba39-102">/errorreport</span></span>
<span data-ttu-id="6ba39-103">[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] コンパイラで内部コンパイル エラーを報告するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="6ba39-103">Specifies how the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler should report internal compiler errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ba39-104">構文</span><span class="sxs-lookup"><span data-stu-id="6ba39-104">Syntax</span></span>  
  
```  
/errorreport:{ prompt | queue | send | none }  
```  
  
## <a name="remarks"></a><span data-ttu-id="6ba39-105">コメント</span><span class="sxs-lookup"><span data-stu-id="6ba39-105">Remarks</span></span>  
 <span data-ttu-id="6ba39-106">このオプションは、レポートする便利な手段を提供、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]を内部コンパイラ エラー (ICE)、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]マイクロソフトのチーム。</span><span class="sxs-lookup"><span data-stu-id="6ba39-106">This option provides a convenient way to report a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] internal compiler error (ICE) to the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] team at Microsoft.</span></span> <span data-ttu-id="6ba39-107">既定では、コンパイラによっていないマイクロソフトに情報。</span><span class="sxs-lookup"><span data-stu-id="6ba39-107">By default, the compiler sends no information to Microsoft.</span></span> <span data-ttu-id="6ba39-108">ただし、内部コンパイラ エラーが発生した場合は、このオプション使用するエラーを Microsoft に報告できます。</span><span class="sxs-lookup"><span data-stu-id="6ba39-108">However, if you do encounter an internal compiler error, this option allows you to report the error to Microsoft.</span></span> <span data-ttu-id="6ba39-109">その情報がマイクロソフトのエンジニアが原因の特定に役立つし、の次回のリリースを向上させるための[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="6ba39-109">That information will help Microsoft engineers identify the cause and may help improve the next release of [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
 <span data-ttu-id="6ba39-110">レポートを送信するユーザーの機能は、コンピューターとユーザー ポリシーのアクセス許可によって異なります。</span><span class="sxs-lookup"><span data-stu-id="6ba39-110">A user's ability to send reports depends on machine and user policy permissions.</span></span>  
  
 <span data-ttu-id="6ba39-111">次の表に、影響、`/errorreport`オプション。</span><span class="sxs-lookup"><span data-stu-id="6ba39-111">The following table summarizes the effect of the `/errorreport` option.</span></span>  
  
|<span data-ttu-id="6ba39-112">オプション</span><span class="sxs-lookup"><span data-stu-id="6ba39-112">Option</span></span>|<span data-ttu-id="6ba39-113">動作</span><span class="sxs-lookup"><span data-stu-id="6ba39-113">Behavior</span></span>|  
|---|---|  
|`prompt`|<span data-ttu-id="6ba39-114">内部コンパイラ エラーが発生した場合、ダイアログ ボックスが、コンパイラが収集された正確なデータを表示できるようにします。</span><span class="sxs-lookup"><span data-stu-id="6ba39-114">If an internal compiler error occurs, a dialog box comes up so that you can view the exact data that the compiler collected.</span></span> <span data-ttu-id="6ba39-115">エラー報告の機密情報があるかを判断し、マイクロソフトに送信するかどうかを判断することできます。</span><span class="sxs-lookup"><span data-stu-id="6ba39-115">You can determine if there is any sensitive information in the error report and make a decision on whether to send it to Microsoft.</span></span> <span data-ttu-id="6ba39-116">送信することを決定する、コンピューターおよびユーザー ポリシー設定で許可する場合、コンパイラは、データを Microsoft に送信します。</span><span class="sxs-lookup"><span data-stu-id="6ba39-116">If you decide to send it, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span>|  
|`queue`|<span data-ttu-id="6ba39-117">エラー レポート キューに入れます。</span><span class="sxs-lookup"><span data-stu-id="6ba39-117">Queues the error report.</span></span> <span data-ttu-id="6ba39-118">前回のログに記録されたエラーを報告するには管理者権限でログインするときに (いない適宜&3; 日間に複数回エラー レポートを送信する)。</span><span class="sxs-lookup"><span data-stu-id="6ba39-118">When you log in with administrator privileges, you can report any failures since the last time you were logged in (you will not be prompted to send reports for failures more than once every three days).</span></span> <span data-ttu-id="6ba39-119">これは、既定の動作と、`/errorreport`オプションが指定されていません。</span><span class="sxs-lookup"><span data-stu-id="6ba39-119">This is the default behavior when the `/errorreport` option is not specified.</span></span>|  
|`send`|<span data-ttu-id="6ba39-120">内部コンパイラ エラーが発生したコンピューターおよびユーザー ポリシー設定で許可する場合は、コンパイラは、データを Microsoft に送信します。</span><span class="sxs-lookup"><span data-stu-id="6ba39-120">If an internal compiler error occurs, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span><br /><br /> <span data-ttu-id="6ba39-121">オプション`/errorReport:send`自動的にエラー情報をマイクロソフトに送信しようとしています。</span><span class="sxs-lookup"><span data-stu-id="6ba39-121">The option `/errorReport:send` attempts to automatically send error information to Microsoft.</span></span> <span data-ttu-id="6ba39-122">このオプションは、レジストリに依存します。</span><span class="sxs-lookup"><span data-stu-id="6ba39-122">This option depends on the registry.</span></span> <span data-ttu-id="6ba39-123">レジストリで適切な値を設定する方法の詳細については、次を参照してください。[を Visual Studio 2008 コマンド ライン ツールでの自動エラー報告を有効にする方法](http://go.microsoft.com/fwlink/?LinkID=184695)します。</span><span class="sxs-lookup"><span data-stu-id="6ba39-123">For more information about setting the appropriate values in the registry, see [How to Turn on Automatic Error Reporting in Visual Studio 2008 Command-line Tools](http://go.microsoft.com/fwlink/?LinkID=184695).</span></span>|  
|`none`|<span data-ttu-id="6ba39-124">内部コンパイラ エラーが発生した場合、収集またはされませんがマイクロソフトに送信します。</span><span class="sxs-lookup"><span data-stu-id="6ba39-124">If an internal compiler error occurs, it will not be collected or sent to Microsoft.</span></span>|  
  
 <span data-ttu-id="6ba39-125">コンパイラは、ソース コードは、通常は、エラー発生時にスタックを含むデータを送信します。</span><span class="sxs-lookup"><span data-stu-id="6ba39-125">The compiler sends data that includes the stack at the time of the error, which usually includes some source code.</span></span> <span data-ttu-id="6ba39-126">場合`/errorreport`と共に使用される、 [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)オプション、ソース ファイル全体が送信されます。</span><span class="sxs-lookup"><span data-stu-id="6ba39-126">If `/errorreport` is used with the [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, then the entire source file is sent.</span></span>  
  
 <span data-ttu-id="6ba39-127">このオプションはで最も多く使用、 [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)オプション、マイクロソフトのエンジニアをより簡単にエラーを再現できるためです。</span><span class="sxs-lookup"><span data-stu-id="6ba39-127">This option is best used with the [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, because it allows Microsoft engineers to more easily reproduce the error.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ba39-128">`/errorreport`オプションは、Visual Studio 開発環境内から使用できません。 コマンドラインからコンパイルする場合だけに利用可能になります。</span><span class="sxs-lookup"><span data-stu-id="6ba39-128">The `/errorreport` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ba39-129">例</span><span class="sxs-lookup"><span data-stu-id="6ba39-129">Example</span></span>  
 <span data-ttu-id="6ba39-130">次のコードをコンパイルしようとしました。 `T2.vb`、コンパイラには、内部コンパイラ エラーが発生すると、エラー レポートを Microsoft に送信することが確認されます。</span><span class="sxs-lookup"><span data-stu-id="6ba39-130">The following code attempts to compile `T2.vb`, and if the compiler encounters an internal compiler error, it prompts you to send the error report to Microsoft.</span></span>  
  
```  
vbc /errorreport:prompt t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="6ba39-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="6ba39-131">See Also</span></span>  
 <span data-ttu-id="6ba39-132">[Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="6ba39-132">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="6ba39-133"> [コンパイル コマンドラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="6ba39-133"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="6ba39-134"> [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)</span><span class="sxs-lookup"><span data-stu-id="6ba39-134"> [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)</span></span>
