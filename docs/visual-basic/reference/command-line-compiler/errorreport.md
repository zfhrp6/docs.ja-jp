---
title: -errorreport
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 59dc833299161eac7b119e654c94534f202b1cb7
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="-errorreport"></a><span data-ttu-id="0481b-102">-errorreport</span><span class="sxs-lookup"><span data-stu-id="0481b-102">-errorreport</span></span>
<span data-ttu-id="0481b-103">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] コンパイラで内部コンパイル エラーを報告するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="0481b-103">Specifies how the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler should report internal compiler errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0481b-104">構文</span><span class="sxs-lookup"><span data-stu-id="0481b-104">Syntax</span></span>  
  
```  
-errorreport:{ prompt | queue | send | none }  
```  
  
## <a name="remarks"></a><span data-ttu-id="0481b-105">コメント</span><span class="sxs-lookup"><span data-stu-id="0481b-105">Remarks</span></span>  
 <span data-ttu-id="0481b-106">このオプションでは、レポートする便利な手段、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]を内部コンパイラ エラー (ICE)、 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Microsoft のチームのです。</span><span class="sxs-lookup"><span data-stu-id="0481b-106">This option provides a convenient way to report a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] internal compiler error (ICE) to the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] team at Microsoft.</span></span> <span data-ttu-id="0481b-107">既定では、コンパイラ情報を送信しませんを Microsoft にします。</span><span class="sxs-lookup"><span data-stu-id="0481b-107">By default, the compiler sends no information to Microsoft.</span></span> <span data-ttu-id="0481b-108">ただし、内部コンパイラ エラーが発生した場合は、このオプションにより、エラーを Microsoft に報告します。</span><span class="sxs-lookup"><span data-stu-id="0481b-108">However, if you do encounter an internal compiler error, this option allows you to report the error to Microsoft.</span></span> <span data-ttu-id="0481b-109">その情報がマイクロソフトのエンジニアが原因の特定に役立つし、次のリリースの改善に役立つ[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="0481b-109">That information will help Microsoft engineers identify the cause and may help improve the next release of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
 <span data-ttu-id="0481b-110">レポートを送信するユーザーの機能は、コンピューターとユーザーのポリシー アクセス許可によって異なります。</span><span class="sxs-lookup"><span data-stu-id="0481b-110">A user's ability to send reports depends on machine and user policy permissions.</span></span>  
  
 <span data-ttu-id="0481b-111">次の表の影響、`-errorreport`オプション。</span><span class="sxs-lookup"><span data-stu-id="0481b-111">The following table summarizes the effect of the `-errorreport` option.</span></span>  
  
|<span data-ttu-id="0481b-112">オプション</span><span class="sxs-lookup"><span data-stu-id="0481b-112">Option</span></span>|<span data-ttu-id="0481b-113">動作</span><span class="sxs-lookup"><span data-stu-id="0481b-113">Behavior</span></span>|  
|---|---|  
|`prompt`|<span data-ttu-id="0481b-114">内部コンパイラ エラーが発生する場合、ダイアログ ボックスが表示されたら、コンパイラが収集される正確なデータを表示できるようにします。</span><span class="sxs-lookup"><span data-stu-id="0481b-114">If an internal compiler error occurs, a dialog box comes up so that you can view the exact data that the compiler collected.</span></span> <span data-ttu-id="0481b-115">エラー報告の機密情報がある場合を判断し、Microsoft に送信するかどうかを判断することできます。</span><span class="sxs-lookup"><span data-stu-id="0481b-115">You can determine if there is any sensitive information in the error report and make a decision on whether to send it to Microsoft.</span></span> <span data-ttu-id="0481b-116">送信することを決定する、コンピューターとユーザー ポリシーの設定で許可する場合は、コンパイラは、データを Microsoft に送信します。</span><span class="sxs-lookup"><span data-stu-id="0481b-116">If you decide to send it, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span>|  
|`queue`|<span data-ttu-id="0481b-117">エラー レポートを待ち行列に入れます。</span><span class="sxs-lookup"><span data-stu-id="0481b-117">Queues the error report.</span></span> <span data-ttu-id="0481b-118">前回のログに記録されたエラーを報告するには管理者特権使用してログインするときに (いない求められます 3 日間に 2 回以上のエラー レポートを送信する)。</span><span class="sxs-lookup"><span data-stu-id="0481b-118">When you log in with administrator privileges, you can report any failures since the last time you were logged in (you will not be prompted to send reports for failures more than once every three days).</span></span> <span data-ttu-id="0481b-119">これは、既定の動作時に、`-errorreport`オプションが指定されていません。</span><span class="sxs-lookup"><span data-stu-id="0481b-119">This is the default behavior when the `-errorreport` option is not specified.</span></span>|  
|`send`|<span data-ttu-id="0481b-120">内部コンパイラ エラーが発生するコンピューターとユーザー ポリシーの設定で許可する場合は、コンパイラは、データを Microsoft に送信します。</span><span class="sxs-lookup"><span data-stu-id="0481b-120">If an internal compiler error occurs, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span><br /><br /> <span data-ttu-id="0481b-121">オプション`-errorreport:send`エラー情報をマイクロソフトに自動的に送信しようとしています。</span><span class="sxs-lookup"><span data-stu-id="0481b-121">The option `-errorreport:send` attempts to automatically send error information to Microsoft.</span></span> <span data-ttu-id="0481b-122">このオプションは、レジストリに依存します。</span><span class="sxs-lookup"><span data-stu-id="0481b-122">This option depends on the registry.</span></span> <span data-ttu-id="0481b-123">レジストリで、適切な値を設定する方法の詳細については、次を参照してください。[を Visual Studio 2008 コマンド ライン ツールで自動エラー報告を有効にする方法](http://go.microsoft.com/fwlink/?LinkID=184695)です。</span><span class="sxs-lookup"><span data-stu-id="0481b-123">For more information about setting the appropriate values in the registry, see [How to Turn on Automatic Error Reporting in Visual Studio 2008 Command-line Tools](http://go.microsoft.com/fwlink/?LinkID=184695).</span></span>|  
|`none`|<span data-ttu-id="0481b-124">内部コンパイラ エラーが発生する場合、収集またはされませんがマイクロソフトに送信します。</span><span class="sxs-lookup"><span data-stu-id="0481b-124">If an internal compiler error occurs, it will not be collected or sent to Microsoft.</span></span>|  
  
 <span data-ttu-id="0481b-125">コンパイラは、通常いくつかのソース コードを含む、エラー発生時にスタックを含むデータを送信します。</span><span class="sxs-lookup"><span data-stu-id="0481b-125">The compiler sends data that includes the stack at the time of the error, which usually includes some source code.</span></span> <span data-ttu-id="0481b-126">場合`-errorreport`と共に使用される、 [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)オプション、ソース ファイル全体が送信されます。</span><span class="sxs-lookup"><span data-stu-id="0481b-126">If `-errorreport` is used with the [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, then the entire source file is sent.</span></span>  
  
 <span data-ttu-id="0481b-127">このオプションを使用して最適な[/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)オプション、マイクロソフトのエンジニアをより簡単にエラーを再現できるためです。</span><span class="sxs-lookup"><span data-stu-id="0481b-127">This option is best used with the [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, because it allows Microsoft engineers to more easily reproduce the error.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0481b-128">`-errorreport`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="0481b-128">The `-errorreport` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0481b-129">例</span><span class="sxs-lookup"><span data-stu-id="0481b-129">Example</span></span>  
 <span data-ttu-id="0481b-130">次のコードをコンパイルしようとしました。 `T2.vb`、コンパイラには、内部コンパイラ エラーが発生すると、エラー レポートを Microsoft に送信することが確認されます。</span><span class="sxs-lookup"><span data-stu-id="0481b-130">The following code attempts to compile `T2.vb`, and if the compiler encounters an internal compiler error, it prompts you to send the error report to Microsoft.</span></span>  
  
```  
vbc -errorreport:prompt t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="0481b-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="0481b-131">See Also</span></span>  
 [<span data-ttu-id="0481b-132">Visual Basic のコマンド ライン コンパイラ</span><span class="sxs-lookup"><span data-stu-id="0481b-132">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="0481b-133">コンパイル コマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="0481b-133">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="0481b-134">-bugreport</span><span class="sxs-lookup"><span data-stu-id="0481b-134">-bugreport</span></span>](../../../visual-basic/reference/command-line-compiler/bugreport.md)
