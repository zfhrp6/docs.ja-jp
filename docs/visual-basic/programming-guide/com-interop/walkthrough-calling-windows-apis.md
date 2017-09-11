---
title: "チュートリアル: Windows Api (Visual Basic) の呼び出し |Microsoft ドキュメント"
ms.custom: 
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
- DLLs, calling
- Windows API, walkthroughs
- platform invoke, walkthroughs
- API calls, walkthroughs [Visual Basic]
- Windows API, calling
- walkthroughs [Visual Basic], API calls
- DllImport attribute, calling Windows API
- Declare statement, declaring DLL functions
ms.assetid: 9280ca96-7a93-47a3-8d01-6d01be0657cb
caps.latest.revision: 20
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
ms.openlocfilehash: ae1ef60e6e27658c872689f5bfe2779493d42e7a
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="walkthrough-calling-windows-apis-visual-basic"></a><span data-ttu-id="ab44c-102">チュートリアル: Windows API の呼び出し (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab44c-102">Walkthrough: Calling Windows APIs (Visual Basic)</span></span>
<span data-ttu-id="ab44c-103">Windows Api は、Windows オペレーティング システムの一部であるダイナミック リンク ライブラリ (Dll) です。</span><span class="sxs-lookup"><span data-stu-id="ab44c-103">Windows APIs are dynamic-link libraries (DLLs) that are part of the Windows operating system.</span></span> <span data-ttu-id="ab44c-104">それらを使用して、独自の同等のプロシージャの作成が困難になる場合は、タスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="ab44c-104">You use them to perform tasks when it is difficult to write equivalent procedures of your own.</span></span> <span data-ttu-id="ab44c-105">たとえば、という名前の関数は、Windows`FlashWindowEx`により、アプリケーションのタイトル バーを薄いおよび濃い網掛けが交互に行うためです。</span><span class="sxs-lookup"><span data-stu-id="ab44c-105">For example, Windows provides a function named `FlashWindowEx` that lets you make the title bar for an application alternate between light and dark shades.</span></span>  
  
 <span data-ttu-id="ab44c-106">コード内の Windows Api を使用する利点は、既に書き込まれている便利な関数が多数用意し、使用するには、待機しているが含まれているために、開発時間を節約することです。</span><span class="sxs-lookup"><span data-stu-id="ab44c-106">The advantage of using Windows APIs in your code is that they can save development time because they contain dozens of useful functions that are already written and waiting to be used.</span></span> <span data-ttu-id="ab44c-107">欠点は、Windows Api は問題が生じた場合やェロェノェを処理できないことがあります。</span><span class="sxs-lookup"><span data-stu-id="ab44c-107">The disadvantage is that Windows APIs can be difficult to work with and unforgiving when things go wrong.</span></span>  
  
 <span data-ttu-id="ab44c-108">Windows Api では、相互運用性の特別なカテゴリを表します。</span><span class="sxs-lookup"><span data-stu-id="ab44c-108">Windows APIs represent a special category of interoperability.</span></span> <span data-ttu-id="ab44c-109">Windows Api では、マネージ コードを使用しないでください、組み込みライブラリを入力し、Visual Studio で使用されるものとは異なるデータ型を使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ab44c-109">Windows APIs do not use managed code, do not have built-in type libraries, and use data types that are different than those used with Visual Studio.</span></span> <span data-ttu-id="ab44c-110">これらの相違点は、Windows Api が COM オブジェクト、Windows Api との相互運用ではないため、および[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]はプラットフォームを使用して実行呼び出すには、pinvoke です。</span><span class="sxs-lookup"><span data-stu-id="ab44c-110">Because of these differences, and because Windows APIs are not COM objects, interoperability with Windows APIs and the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] is performed using platform invoke, or PInvoke.</span></span> <span data-ttu-id="ab44c-111">プラットフォーム呼び出しはマネージ Dll に実装されているアンマネージ関数を呼び出すコードを有効にするサービスです。</span><span class="sxs-lookup"><span data-stu-id="ab44c-111">Platform invoke is a service that enables managed code to call unmanaged functions implemented in DLLs.</span></span> <span data-ttu-id="ab44c-112">詳細については、次を参照してください。[アンマネージ DLL 関数の処理](http://msdn.microsoft.com/library/eca7606e-ebfb-4f47-b8d9-289903fdc045)します。</span><span class="sxs-lookup"><span data-stu-id="ab44c-112">For more information, see [Consuming Unmanaged DLL Functions](http://msdn.microsoft.com/library/eca7606e-ebfb-4f47-b8d9-289903fdc045).</span></span> <span data-ttu-id="ab44c-113">PInvoke を使用することができます[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]を使用して、`Declare`ステートメントまたは適用する、`DllImport`属性を空のプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="ab44c-113">You can use PInvoke in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] by using either the `Declare` statement or applying the `DllImport` attribute to an empty procedure.</span></span>  
  
 <span data-ttu-id="ab44c-114">Windows API の呼び出しの重要な部分のされた[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]、過去のプログラミングしますが、することはまれで必要な[!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="ab44c-114">Windows API calls were an important part of [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programming in the past, but are seldom necessary with [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)].</span></span> <span data-ttu-id="ab44c-115">可能であればからマネージ コードを使用する必要があります、 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] Windows API の呼び出しではなく、タスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="ab44c-115">Whenever possible, you should use managed code from the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] to perform tasks, instead of Windows API calls.</span></span> <span data-ttu-id="ab44c-116">このチュートリアルは、使用する必要のある状況についての情報を Windows Api が必要です。</span><span class="sxs-lookup"><span data-stu-id="ab44c-116">This walkthrough provides information for those situations in which using Windows APIs is necessary.</span></span>  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## <a name="api-calls-using-declare"></a><span data-ttu-id="ab44c-117">使用して、API 呼び出しを宣言します。</span><span class="sxs-lookup"><span data-stu-id="ab44c-117">API Calls Using Declare</span></span>  
 <span data-ttu-id="ab44c-118">Windows Api を呼び出す最も一般的な方法を使用して、`Declare`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="ab44c-118">The most common way to call Windows APIs is by using the `Declare` statement.</span></span>  
  
#### <a name="to-declare-a-dll-procedure"></a><span data-ttu-id="ab44c-119">DLL のプロシージャを宣言するには</span><span class="sxs-lookup"><span data-stu-id="ab44c-119">To declare a DLL procedure</span></span>  
  
1.  <span data-ttu-id="ab44c-120">呼び出すには、必要な関数とその引数、引数の型の名前を特定し、値、だけでなく、名前、およびそれを含んでいる DLL の場所を返します。</span><span class="sxs-lookup"><span data-stu-id="ab44c-120">Determine the name of the function you want to call, plus its arguments, argument types, and return value, as well as the name and location of the DLL that contains it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ab44c-121">Windows Api についての詳細については、プラットフォーム SDK の Windows API で Win32 SDK ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab44c-121">For complete information about the Windows APIs, see the Win32 SDK documentation in the Platform SDK Windows API.</span></span> <span data-ttu-id="ab44c-122">Windows Api を使用する定数についての詳細については、Windows.h、Platform SDK に含まれているなどのヘッダー ファイルを調べてください。</span><span class="sxs-lookup"><span data-stu-id="ab44c-122">For more information about the constants that Windows APIs use, examine the header files such as Windows.h included with the Platform SDK.</span></span>  
  
2.  <span data-ttu-id="ab44c-123">クリックして新しい Windows アプリケーション プロジェクトを開きます**新規**上、**ファイル**] メニューの [クリックして**プロジェクト**します。</span><span class="sxs-lookup"><span data-stu-id="ab44c-123">Open a new Windows Application project by clicking **New** on the **File** menu, and then clicking **Project**.</span></span> <span data-ttu-id="ab44c-124">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ab44c-124">The **New Project** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="ab44c-125">選択**Windows アプリケーション**の一覧から[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プロジェクト テンプレートです。</span><span class="sxs-lookup"><span data-stu-id="ab44c-125">Select **Windows Application** from the list of [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] project templates.</span></span> <span data-ttu-id="ab44c-126">新しいプロジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ab44c-126">The new project is displayed.</span></span>  
  
4.  <span data-ttu-id="ab44c-127">次の追加`Declare`クラスまたは DLL を使用するモジュールのいずれかの機能します。</span><span class="sxs-lookup"><span data-stu-id="ab44c-127">Add the following `Declare` function either to the class or module in which you want to use the DLL:</span></span>  
  
     <span data-ttu-id="ab44c-128">[!code-vb[VbVbalrInterop&#9;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="ab44c-128">[!code-vb[VbVbalrInterop#9](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_1.vb)]</span></span>  
  
### <a name="parts-of-the-declare-statement"></a><span data-ttu-id="ab44c-129">部分、Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="ab44c-129">Parts of the Declare Statement</span></span>  
 <span data-ttu-id="ab44c-130">`Declare`ステートメントには、次の要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ab44c-130">The `Declare` statement includes the following elements.</span></span>  
  
#### <a name="auto-modifier"></a><span data-ttu-id="ab44c-131">Auto 修飾子</span><span class="sxs-lookup"><span data-stu-id="ab44c-131">Auto modifier</span></span>  
 <span data-ttu-id="ab44c-132">`Auto`修飾子が共通言語ランタイムの規則 (またはエイリアス名を指定する場合) に従って、メソッド名に基づく文字列に変換するようランタイムに指示します。</span><span class="sxs-lookup"><span data-stu-id="ab44c-132">The `Auto` modifier instructs the runtime to convert the string based on the method name according to common language runtime rules (or alias name if specified).</span></span>  
  
#### <a name="lib-and-alias-keywords"></a><span data-ttu-id="ab44c-133">Lib とエイリアスのキーワード</span><span class="sxs-lookup"><span data-stu-id="ab44c-133">Lib and Alias keywords</span></span>  
 <span data-ttu-id="ab44c-134">名前の次の`Function`キーワードは、インポートされた関数にアクセスするプログラムで使用される名前です。</span><span class="sxs-lookup"><span data-stu-id="ab44c-134">The name following the `Function` keyword is the name your program uses to access the imported function.</span></span> <span data-ttu-id="ab44c-135">を呼び出す関数の実際の名前と同じことができますか、任意の有効なプロシージャの名前と、採用を使用する、`Alias`キーワードを呼び出している関数の実際の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="ab44c-135">It can be the same as the real name of the function you are calling, or you can use any valid procedure name and then employ the `Alias` keyword to specify the real name of the function you are calling.</span></span>  
  
 <span data-ttu-id="ab44c-136">指定の`Lib`キーワードを呼び出している関数を含んでいる DLL の場所と名前。</span><span class="sxs-lookup"><span data-stu-id="ab44c-136">Specify the `Lib` keyword, followed by the name and location of the DLL that contains the function you are calling.</span></span> <span data-ttu-id="ab44c-137">Windows システム ディレクトリ内にあるファイルのパスを指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ab44c-137">You do not need to specify the path for files located in the Windows system directories.</span></span>  
  
 <span data-ttu-id="ab44c-138">使用して、`Alias`を呼び出している関数の名前が有効な場合は、キーワード[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プロシージャ名、または、アプリケーションでは、その他の項目の名前と競合します。</span><span class="sxs-lookup"><span data-stu-id="ab44c-138">Use the `Alias` keyword if the name of the function you are calling is not a valid [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] procedure name, or conflicts with the name of other items in your application.</span></span> <span data-ttu-id="ab44c-139">`Alias`呼び出される関数の本当の名前を示します。</span><span class="sxs-lookup"><span data-stu-id="ab44c-139">`Alias` indicates the true name of the function being called.</span></span>  
  
#### <a name="argument-and-data-type-declarations"></a><span data-ttu-id="ab44c-140">引数とデータ型の宣言</span><span class="sxs-lookup"><span data-stu-id="ab44c-140">Argument and Data Type Declarations</span></span>  
 <span data-ttu-id="ab44c-141">引数とそのデータ型を宣言します。</span><span class="sxs-lookup"><span data-stu-id="ab44c-141">Declare the arguments and their data types.</span></span> <span data-ttu-id="ab44c-142">この部分は、Windows で使用されるデータ型は、Visual Studio のデータ型に対応していないために、困難な場合ことができます。</span><span class="sxs-lookup"><span data-stu-id="ab44c-142">This part can be challenging because the data types that Windows uses do not correspond to Visual Studio data types.</span></span> [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="ab44c-143">この自動化は多くの作業を互換性のあるデータ型と呼ばれるプロセスに引数を変換する*マーシャ リング*します。</span><span class="sxs-lookup"><span data-stu-id="ab44c-143"> does a lot of the work for you by converting arguments to compatible data types, a process called *marshaling*.</span></span> <span data-ttu-id="ab44c-144">使用して引数をマーシャ リングする方法を明示的に制御できる、<xref:System.Runtime.InteropServices.MarshalAsAttribute>属性で定義されている、<xref:System.Runtime.InteropServices>名前空間</xref:System.Runtime.InteropServices></xref:System.Runtime.InteropServices.MarshalAsAttribute>。</span><span class="sxs-lookup"><span data-stu-id="ab44c-144">You can explicitly control how arguments are marshaled by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute defined in the <xref:System.Runtime.InteropServices> namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab44c-145">以前のバージョンの[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]パラメーターを宣言することができる`As Any`、つまり、すべてのデータのデータ型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ab44c-145">Previous versions of [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] allowed you to declare parameters `As Any`, meaning that data of any data type could be used.</span></span> [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="ab44c-146">すべての特定のデータ型を使用することが必要です。`Declare`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="ab44c-146"> requires that you use a specific data type for all `Declare` statements.</span></span>  
  
#### <a name="windows-api-constants"></a><span data-ttu-id="ab44c-147">Windows API の定数</span><span class="sxs-lookup"><span data-stu-id="ab44c-147">Windows API Constants</span></span>  
 <span data-ttu-id="ab44c-148">いくつかの引数は、定数の組み合わせです。</span><span class="sxs-lookup"><span data-stu-id="ab44c-148">Some arguments are combinations of constants.</span></span> <span data-ttu-id="ab44c-149">たとえば、`MessageBox`このチュートリアルで示すように API と呼ばれる整数の引数を受け取る`Typ`メッセージ ボックスを表示する方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="ab44c-149">For example, the `MessageBox` API shown in this walkthrough accepts an integer argument called `Typ` that controls how the message box is displayed.</span></span> <span data-ttu-id="ab44c-150">確認するには、これらの定数の数値を指定できます、 `#define` WinUser.h ファイル内のステートメントです。</span><span class="sxs-lookup"><span data-stu-id="ab44c-150">You can determine the numeric value of these constants by examining the `#define` statements in the file WinUser.h.</span></span> <span data-ttu-id="ab44c-151">数値の値は、電卓を使用してそれらを追加し、10 進数に変換するために一般的に&16; 進数で表示されます。</span><span class="sxs-lookup"><span data-stu-id="ab44c-151">The numeric values are generally shown in hexadecimal, so you may want to use a calculator to add them and convert to decimal.</span></span> <span data-ttu-id="ab44c-152">例では、感嘆符スタイルの定数を結合する場合の`MB_ICONEXCLAMATION`0x00000030 し、はい/スタイルなし`MB_YESNO`0x00000004、番号を追加し、10 進数、0x00000034 または 52 の結果を取得します。</span><span class="sxs-lookup"><span data-stu-id="ab44c-152">For example, if you want to combine the constants for the exclamation style `MB_ICONEXCLAMATION` 0x00000030 and the Yes/No style `MB_YESNO` 0x00000004, you can add the numbers and get a result of 0x00000034, or 52 decimal.</span></span> <span data-ttu-id="ab44c-153">これらの値をアプリケーションで定数として宣言し、それらを結合することをお勧め&10; 進数の結果を直接使用できますを使用して、`Or`演算子。</span><span class="sxs-lookup"><span data-stu-id="ab44c-153">Although you can use the decimal result directly, it is better to declare these values as constants in your application and combine them using the `Or` operator.</span></span>  
  
###### <a name="to-declare-constants-for-windows-api-calls"></a><span data-ttu-id="ab44c-154">Windows API の呼び出しの定数を宣言するには</span><span class="sxs-lookup"><span data-stu-id="ab44c-154">To declare constants for Windows API calls</span></span>  
  
1.  <span data-ttu-id="ab44c-155">Windows 関数の呼び出しと、ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ab44c-155">Consult the documentation for the Windows function you are calling.</span></span> <span data-ttu-id="ab44c-156">使用されている定数の名前とこれらの定数の数値を含む .h ファイルの名前を決定します。</span><span class="sxs-lookup"><span data-stu-id="ab44c-156">Determine the name of the constants it uses and the name of the .h file that contains the numeric values for these constants.</span></span>  
  
2.  <span data-ttu-id="ab44c-157">メモ帳などのテキスト エディターを使用して、ヘッダー (.h) ファイルの内容を表示しを使用している定数に関連付けられている値を検索します。</span><span class="sxs-lookup"><span data-stu-id="ab44c-157">Use a text editor, such as Notepad, to view the contents of the header (.h) file, and find the values associated with the constants you are using.</span></span> <span data-ttu-id="ab44c-158">たとえば、 `MessageBox` API は、定数を使用して`MB_ICONQUESTION`メッセージ ボックスに疑問符 () を表示します。</span><span class="sxs-lookup"><span data-stu-id="ab44c-158">For example, the `MessageBox` API uses the constant `MB_ICONQUESTION` to show a question mark in the message box.</span></span> <span data-ttu-id="ab44c-159">定義を`MB_ICONQUESTION`WinUser.h にあり、次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="ab44c-159">The definition for `MB_ICONQUESTION` is in WinUser.h and appears as follows:</span></span>  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3.  <span data-ttu-id="ab44c-160">それと同等の追加`Const`ステートメントをクラスまたはモジュールをこれらの定数をアプリケーションで使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="ab44c-160">Add equivalent `Const` statements to your class or module to make these constants available to your application.</span></span> <span data-ttu-id="ab44c-161">例:</span><span class="sxs-lookup"><span data-stu-id="ab44c-161">For example:</span></span>  
  
     <span data-ttu-id="ab44c-162">[!code-vb[VbVbalrInterop&#11;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="ab44c-162">[!code-vb[VbVbalrInterop#11](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_2.vb)]</span></span>  
  
###### <a name="to-call-the-dll-procedure"></a><span data-ttu-id="ab44c-163">DLL のプロシージャを呼び出す</span><span class="sxs-lookup"><span data-stu-id="ab44c-163">To call the DLL procedure</span></span>  
  
1.  <span data-ttu-id="ab44c-164">という名前のボタンを追加`Button1`の起動時に、プロジェクトの形式し、すると、そのコードを表示する をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="ab44c-164">Add a button named `Button1` to the startup form for your project, and then double-click it to view its code.</span></span> <span data-ttu-id="ab44c-165">ボタンのイベント ハンドラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ab44c-165">The event handler for the button is displayed.</span></span>  
  
2.  <span data-ttu-id="ab44c-166">コードを追加して、`Click`プロシージャを呼び出すし、適切な引数を提供する、追加したボタンのイベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="ab44c-166">Add code to the `Click` event handler for the button you added, to call the procedure and provide the appropriate arguments:</span></span>  
  
     <span data-ttu-id="ab44c-167">[!code-vb[VbVbalrInterop&#12;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="ab44c-167">[!code-vb[VbVbalrInterop#12](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_3.vb)]</span></span>  
  
3.  <span data-ttu-id="ab44c-168">F5 キーを押して、プロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="ab44c-168">Run the project by pressing F5.</span></span> <span data-ttu-id="ab44c-169">両方で、メッセージ ボックスが表示**はい**と**いいえ**返信ボタン。</span><span class="sxs-lookup"><span data-stu-id="ab44c-169">The message box is displayed with both **Yes** and **No** response buttons.</span></span> <span data-ttu-id="ab44c-170">いずれかをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ab44c-170">Click either one.</span></span>  
  
#### <a name="data-marshaling"></a><span data-ttu-id="ab44c-171">データ マーシャ リング</span><span class="sxs-lookup"><span data-stu-id="ab44c-171">Data Marshaling</span></span>  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="ab44c-172">自動的に変換パラメーターと Windows API の呼び出しの戻り値のデータ型使える、 `MarshalAs` API のものと想定するアンマネージ データ型を明示的に指定する属性です。</span><span class="sxs-lookup"><span data-stu-id="ab44c-172"> automatically converts the data types of parameters and return values for Windows API calls, but you can use the `MarshalAs` attribute to explicitly specify unmanaged data types that an API expects.</span></span> <span data-ttu-id="ab44c-173">相互運用マーシャ リングの詳細については、次を参照してください。[相互運用マーシャ リング](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)します。</span><span class="sxs-lookup"><span data-stu-id="ab44c-173">For more information about interop marshaling, see [Interop Marshaling](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a).</span></span>  
  
###### <a name="to-use-declare-and-marshalas-in-an-api-call"></a><span data-ttu-id="ab44c-174">Declare と MarshalAs API 呼び出しで使用するには</span><span class="sxs-lookup"><span data-stu-id="ab44c-174">To use Declare and MarshalAs in an API call</span></span>  
  
1.  <span data-ttu-id="ab44c-175">データ型を引数、呼び出そうと関数の名前を特定し、値を返します。</span><span class="sxs-lookup"><span data-stu-id="ab44c-175">Determine the name of the function you want to call, plus its arguments, data types, and return value.</span></span>  
  
2.  <span data-ttu-id="ab44c-176">アクセスを簡略化する、`MarshalAs`属性は、追加、`Imports`ステートメントをクラスまたは次の例のように、モジュールに対するコードの上部にします。</span><span class="sxs-lookup"><span data-stu-id="ab44c-176">To simplify access to the `MarshalAs` attribute, add an `Imports` statement to the top of the code for the class or module, as in the following example:</span></span>  
  
     <span data-ttu-id="ab44c-177">[!code-vb[VbVbalrInterop&#13;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="ab44c-177">[!code-vb[VbVbalrInterop#13](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]</span></span>  
  
3.  <span data-ttu-id="ab44c-178">クラスまたはモジュールを使用しているし、適用、インポートされた関数に対する関数プロトタイプを追加、`MarshalAs`属性をパラメーターまたは戻り値。</span><span class="sxs-lookup"><span data-stu-id="ab44c-178">Add a function prototype for the imported function to the class or module you are using, and apply the `MarshalAs` attribute to the parameters or return value.</span></span> <span data-ttu-id="ab44c-179">次の例では、型が必要ですが、API 呼び出しで`void*`としてマーシャ リング`AsAny`:</span><span class="sxs-lookup"><span data-stu-id="ab44c-179">In the following example, an API call that expects the type `void*` is marshaled as `AsAny`:</span></span>  
  
     <span data-ttu-id="ab44c-180">[!code-vb[VbVbalrInterop&#14;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="ab44c-180">[!code-vb[VbVbalrInterop#14](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_5.vb)]</span></span>  
  
## <a name="api-calls-using-dllimport"></a><span data-ttu-id="ab44c-181">DllImport を使用する API 呼び出し</span><span class="sxs-lookup"><span data-stu-id="ab44c-181">API Calls Using DllImport</span></span>  
 <span data-ttu-id="ab44c-182">`DllImport`属性は、タイプ ライブラリを持たない Dll で関数を呼び出す&2; 番目の方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="ab44c-182">The `DllImport` attribute provides a second way to call functions in DLLs without type libraries.</span></span> <span data-ttu-id="ab44c-183">`DllImport`使用するとほぼ同じですが、`Declare`ステートメントが関数を呼び出す方法より詳細に制御を提供します。</span><span class="sxs-lookup"><span data-stu-id="ab44c-183">`DllImport` is roughly equivalent to using a `Declare` statement but provides more control over how functions are called.</span></span>  
  
 <span data-ttu-id="ab44c-184">使用する`DllImport`ほとんどの Windows API を使用、呼び出しは、共有を参照する限りを呼び出します (とも呼ばれる*静的*) メソッドです。</span><span class="sxs-lookup"><span data-stu-id="ab44c-184">You can use `DllImport` with most Windows API calls as long as the call refers to a shared (sometimes called *static*) method.</span></span> <span data-ttu-id="ab44c-185">クラスのインスタンスを必要とするメソッドを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="ab44c-185">You cannot use methods that require an instance of a class.</span></span> <span data-ttu-id="ab44c-186">異なり`Declare`ステートメント、`DllImport`呼び出しを使用できない、`MarshalAs`属性です。</span><span class="sxs-lookup"><span data-stu-id="ab44c-186">Unlike `Declare` statements, `DllImport` calls cannot use the `MarshalAs` attribute.</span></span>  
  
#### <a name="to-call-a-windows-api-using-the-dllimport-attribute"></a><span data-ttu-id="ab44c-187">DllImport 属性を使用して Windows API を呼び出す</span><span class="sxs-lookup"><span data-stu-id="ab44c-187">To call a Windows API using the DllImport attribute</span></span>  
  
1.  <span data-ttu-id="ab44c-188">クリックして新しい Windows アプリケーション プロジェクトを開きます**新規**上、**ファイル**] メニューの [クリックして**プロジェクト**します。</span><span class="sxs-lookup"><span data-stu-id="ab44c-188">Open a new Windows Application project by clicking **New** on the **File** menu, and then clicking **Project**.</span></span> <span data-ttu-id="ab44c-189">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ab44c-189">The **New Project** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="ab44c-190">選択**Windows アプリケーション**の一覧から[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プロジェクト テンプレートです。</span><span class="sxs-lookup"><span data-stu-id="ab44c-190">Select **Windows Application** from the list of [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] project templates.</span></span> <span data-ttu-id="ab44c-191">新しいプロジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ab44c-191">The new project is displayed.</span></span>  
  
3.  <span data-ttu-id="ab44c-192">という名前のボタンを追加`Button2`スタートアップ フォームにします。</span><span class="sxs-lookup"><span data-stu-id="ab44c-192">Add a button named `Button2` to the startup form.</span></span>  
  
4.  <span data-ttu-id="ab44c-193">ダブルクリックして`Button2`フォームのコード ビューを開きます。</span><span class="sxs-lookup"><span data-stu-id="ab44c-193">Double-click `Button2` to open the code view for the form.</span></span>  
  
5.  <span data-ttu-id="ab44c-194">アクセスを簡略化する`DllImport`、追加、`Imports`ステートメントをスタートアップ フォーム クラスのコードの上部にします。</span><span class="sxs-lookup"><span data-stu-id="ab44c-194">To simplify access to `DllImport`, add an `Imports` statement to the top of the code for the startup form class:</span></span>  
  
     <span data-ttu-id="ab44c-195">[!code-vb[VbVbalrInterop&#13;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="ab44c-195">[!code-vb[VbVbalrInterop#13](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]</span></span>  
  
6.  <span data-ttu-id="ab44c-196">この空の関数を宣言、`End Class`フォーム、および関数の名前に対する`MoveFile`します。</span><span class="sxs-lookup"><span data-stu-id="ab44c-196">Declare an empty function preceding the `End Class` statement for the form, and name the function `MoveFile`.</span></span>  
  
7.  <span data-ttu-id="ab44c-197">適用、`Public`と`Shared`関数宣言とパラメーターを設定する修飾子`MoveFile`Windows API 関数を使用して、引数に基づいた。</span><span class="sxs-lookup"><span data-stu-id="ab44c-197">Apply the `Public` and `Shared` modifiers to the function declaration and set parameters for `MoveFile` based on the arguments the Windows API function uses:</span></span>  
  
     <span data-ttu-id="ab44c-198">[!code-vb[VbVbalrInterop&#16;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="ab44c-198">[!code-vb[VbVbalrInterop#16](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_6.vb)]</span></span>  
  
     <span data-ttu-id="ab44c-199">関数は、任意の有効なプロシージャ名前を設定できます。`DllImport`属性は、DLL の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="ab44c-199">Your function can have any valid procedure name; the `DllImport` attribute specifies the name in the DLL.</span></span> <span data-ttu-id="ab44c-200">パラメーターのマーシャ リングの相互運用性も処理やデータに類似する Visual Studio のデータ型を選択できるように、戻り値の型 API によって使用されるあります。</span><span class="sxs-lookup"><span data-stu-id="ab44c-200">It also handles interoperability marshaling for the parameters and return values, so you can choose Visual Studio data types that are similar to the data types the API uses.</span></span>  
  
8.  <span data-ttu-id="ab44c-201">適用、`DllImport`属性を空の関数にします。</span><span class="sxs-lookup"><span data-stu-id="ab44c-201">Apply the `DllImport` attribute to the empty function.</span></span> <span data-ttu-id="ab44c-202">最初のパラメーターは、呼び出し先関数を含んでいる DLL の場所と名前です。</span><span class="sxs-lookup"><span data-stu-id="ab44c-202">The first parameter is the name and location of the DLL containing the function you are calling.</span></span> <span data-ttu-id="ab44c-203">Windows システム ディレクトリ内にあるファイルのパスを指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ab44c-203">You do not need to specify the path for files located in the Windows system directories.</span></span> <span data-ttu-id="ab44c-204">2 番目のパラメーターは、Windows API の関数の名前を指定する名前付き引数です。</span><span class="sxs-lookup"><span data-stu-id="ab44c-204">The second parameter is a named argument that specifies the name of the function in the Windows API.</span></span> <span data-ttu-id="ab44c-205">この例では、`DllImport`属性への呼び出しを強制する`MoveFile`に転送される`MoveFileW`KERNEL32 にします。DLL です。</span><span class="sxs-lookup"><span data-stu-id="ab44c-205">In this example, the `DllImport` attribute forces calls to `MoveFile` to be forwarded to `MoveFileW` in KERNEL32.DLL.</span></span> <span data-ttu-id="ab44c-206">`MoveFileW`メソッドは、パスからファイルをコピー`src`パスに`dst`します。</span><span class="sxs-lookup"><span data-stu-id="ab44c-206">The `MoveFileW` method copies a file from the path `src` to the path `dst`.</span></span>  
  
     <span data-ttu-id="ab44c-207">[!code-vb[VbVbalrInterop&17;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="ab44c-207">[!code-vb[VbVbalrInterop#17](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_7.vb)]</span></span>  
  
9. <span data-ttu-id="ab44c-208">コードを追加して、`Button2_Click`イベント ハンドラー関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="ab44c-208">Add code to the `Button2_Click` event handler to call the function:</span></span>  
  
     <span data-ttu-id="ab44c-209">[!code-vb[VbVbalrInterop&#18;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="ab44c-209">[!code-vb[VbVbalrInterop#18](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_8.vb)]</span></span>  
  
10. <span data-ttu-id="ab44c-210">Test.txt という名前のファイルを作成し、ハード ドライブ上の C:\Tmp ディレクトリに配置します。</span><span class="sxs-lookup"><span data-stu-id="ab44c-210">Create a file named Test.txt and place it in the C:\Tmp directory on your hard drive.</span></span> <span data-ttu-id="ab44c-211">必要な場合は、Tmp ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="ab44c-211">Create the Tmp directory if necessary.</span></span>  
  
11. <span data-ttu-id="ab44c-212">F5 キーを押してアプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="ab44c-212">Press F5 to start the application.</span></span> <span data-ttu-id="ab44c-213">メイン フォームが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ab44c-213">The main form appears.</span></span>  
  
12. <span data-ttu-id="ab44c-214">クリックして**Button2**します。</span><span class="sxs-lookup"><span data-stu-id="ab44c-214">Click **Button2**.</span></span> <span data-ttu-id="ab44c-215">ファイルを移動できる場合は、「ファイルが正常に移動されました」メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ab44c-215">The message "The file was moved successfully" is displayed if the file can be moved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab44c-216">関連項目</span><span class="sxs-lookup"><span data-stu-id="ab44c-216">See Also</span></span>  
 <span data-ttu-id="ab44c-217"><xref:System.Runtime.InteropServices.DllImportAttribute></xref:System.Runtime.InteropServices.DllImportAttribute></span><span class="sxs-lookup"><span data-stu-id="ab44c-217"><xref:System.Runtime.InteropServices.DllImportAttribute></span></span>   
 <span data-ttu-id="ab44c-218"><xref:System.Runtime.InteropServices.MarshalAsAttribute></xref:System.Runtime.InteropServices.MarshalAsAttribute></span><span class="sxs-lookup"><span data-stu-id="ab44c-218"><xref:System.Runtime.InteropServices.MarshalAsAttribute></span></span>   
<span data-ttu-id="ab44c-219"> [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md) </span><span class="sxs-lookup"><span data-stu-id="ab44c-219"> [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) </span></span>  
<span data-ttu-id="ab44c-220"> [自動](../../../visual-basic/language-reference/modifiers/auto.md) </span><span class="sxs-lookup"><span data-stu-id="ab44c-220"> [Auto](../../../visual-basic/language-reference/modifiers/auto.md) </span></span>  
<span data-ttu-id="ab44c-221"> [エイリアス](../../../visual-basic/language-reference/statements/alias-clause.md) </span><span class="sxs-lookup"><span data-stu-id="ab44c-221"> [Alias](../../../visual-basic/language-reference/statements/alias-clause.md) </span></span>  
<span data-ttu-id="ab44c-222"> [COM 相互運用機能](../../../visual-basic/programming-guide/com-interop/index.md) </span><span class="sxs-lookup"><span data-stu-id="ab44c-222"> [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md) </span></span>  
<span data-ttu-id="ab44c-223"> [マネージ コードでのプロトタイプの作成](http://msdn.microsoft.com/library/ecdcf25d-cae3-4f07-a2b6-8397ac6dc42d) </span><span class="sxs-lookup"><span data-stu-id="ab44c-223"> [Creating Prototypes in Managed Code](http://msdn.microsoft.com/library/ecdcf25d-cae3-4f07-a2b6-8397ac6dc42d) </span></span>  
<span data-ttu-id="ab44c-224"> [コールバック メソッドとしてデリゲートのマーシャ リング](http://msdn.microsoft.com/library/6ddd7866-9804-4571-84de-83f5cc017a5a)</span><span class="sxs-lookup"><span data-stu-id="ab44c-224"> [Marshaling a Delegate as a Callback Method](http://msdn.microsoft.com/library/6ddd7866-9804-4571-84de-83f5cc017a5a)</span></span>
