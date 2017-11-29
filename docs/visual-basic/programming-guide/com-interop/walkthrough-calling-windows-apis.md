---
title: "チュートリアル: Windows API の呼び出し (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- DLLs, calling
- Windows API, walkthroughs
- platform invoke, walkthroughs
- API calls [Visual Basic], walkthroughs [Visual Basic]
- Windows API, calling
- walkthroughs [Visual Basic], API calls
- DllImport attribute, calling Windows API
- Declare statement [Visual Basic], declaring DLL functions
ms.assetid: 9280ca96-7a93-47a3-8d01-6d01be0657cb
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d494ad0f8bd4eb0dac57de214064fd2d208011ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-calling-windows-apis-visual-basic"></a><span data-ttu-id="70881-102">チュートリアル: Windows API の呼び出し (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70881-102">Walkthrough: Calling Windows APIs (Visual Basic)</span></span>
<span data-ttu-id="70881-103">Windows Api は、Windows オペレーティング システムの一部であるダイナミック リンク ライブラリ (Dll) です。</span><span class="sxs-lookup"><span data-stu-id="70881-103">Windows APIs are dynamic-link libraries (DLLs) that are part of the Windows operating system.</span></span> <span data-ttu-id="70881-104">それらを使用して、タスクを実行するときは、独自の同等のプロシージャを記述することは困難です。</span><span class="sxs-lookup"><span data-stu-id="70881-104">You use them to perform tasks when it is difficult to write equivalent procedures of your own.</span></span> <span data-ttu-id="70881-105">たとえば、という名前の関数は、Windows`FlashWindowEx`をアプリケーションのタイトル バーを薄いおよび濃い網掛けが交互に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="70881-105">For example, Windows provides a function named `FlashWindowEx` that lets you make the title bar for an application alternate between light and dark shades.</span></span>  
  
 <span data-ttu-id="70881-106">コード内の Windows Api を使用する利点は、含んでいるため、数十個は既に書き込まれている便利な関数の待機しているために使用する開発にかかる時間を保存することができます。</span><span class="sxs-lookup"><span data-stu-id="70881-106">The advantage of using Windows APIs in your code is that they can save development time because they contain dozens of useful functions that are already written and waiting to be used.</span></span> <span data-ttu-id="70881-107">欠点は、Windows Api が困難で動作する厳格問題が生じたときにできることです。</span><span class="sxs-lookup"><span data-stu-id="70881-107">The disadvantage is that Windows APIs can be difficult to work with and unforgiving when things go wrong.</span></span>  
  
 <span data-ttu-id="70881-108">Windows Api では、相互運用性の特殊なカテゴリを表します。</span><span class="sxs-lookup"><span data-stu-id="70881-108">Windows APIs represent a special category of interoperability.</span></span> <span data-ttu-id="70881-109">Windows Api では、マネージ コードを使用しない、組み込みタイプ ライブラリ、および Visual Studio で使用されるものとは異なるデータ型を使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="70881-109">Windows APIs do not use managed code, do not have built-in type libraries, and use data types that are different than those used with Visual Studio.</span></span> <span data-ttu-id="70881-110">これらの相違のための Windows Api は、Windows Api との相互運用、COM オブジェクトではないため、および[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]プラットフォームを使用して実行呼び出すには、または PInvoke です。</span><span class="sxs-lookup"><span data-stu-id="70881-110">Because of these differences, and because Windows APIs are not COM objects, interoperability with Windows APIs and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] is performed using platform invoke, or PInvoke.</span></span> <span data-ttu-id="70881-111">プラットフォーム呼び出しはマネージ Dll に実装されているアンマネージ関数を呼び出すコードを有効にするサービスです。</span><span class="sxs-lookup"><span data-stu-id="70881-111">Platform invoke is a service that enables managed code to call unmanaged functions implemented in DLLs.</span></span> <span data-ttu-id="70881-112">詳細については、次を参照してください。[アンマネージ DLL 関数の使用](../../../framework/interop/consuming-unmanaged-dll-functions.md)です。</span><span class="sxs-lookup"><span data-stu-id="70881-112">For more information, see [Consuming Unmanaged DLL Functions](../../../framework/interop/consuming-unmanaged-dll-functions.md).</span></span> <span data-ttu-id="70881-113">PInvoke を使用する[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]いずれかを使用して、`Declare`ステートメントまたは適用する、`DllImport`属性を空のプロシージャです。</span><span class="sxs-lookup"><span data-stu-id="70881-113">You can use PInvoke in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] by using either the `Declare` statement or applying the `DllImport` attribute to an empty procedure.</span></span>  
  
 <span data-ttu-id="70881-114">Windows API の呼び出しがの重要な部分[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]過去のプログラミングしますが、めったに必要な Visual Basic .NET でします。</span><span class="sxs-lookup"><span data-stu-id="70881-114">Windows API calls were an important part of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programming in the past, but are seldom necessary with Visual Basic .NET.</span></span> <span data-ttu-id="70881-115">マネージ コードを使用する必要があります、可能な限り、 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Windows API の呼び出しではなく、タスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="70881-115">Whenever possible, you should use managed code from the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] to perform tasks, instead of Windows API calls.</span></span> <span data-ttu-id="70881-116">このチュートリアルで使用する必要のある状況についての情報は Windows Api が必要です。</span><span class="sxs-lookup"><span data-stu-id="70881-116">This walkthrough provides information for those situations in which using Windows APIs is necessary.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="api-calls-using-declare"></a><span data-ttu-id="70881-117">API 呼び出しを使用して宣言します。</span><span class="sxs-lookup"><span data-stu-id="70881-117">API Calls Using Declare</span></span>  
 <span data-ttu-id="70881-118">Windows Api を呼び出して最も一般的な方法を使用して、`Declare`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="70881-118">The most common way to call Windows APIs is by using the `Declare` statement.</span></span>  
  
#### <a name="to-declare-a-dll-procedure"></a><span data-ttu-id="70881-119">DLL のプロシージャを宣言するには</span><span class="sxs-lookup"><span data-stu-id="70881-119">To declare a DLL procedure</span></span>  
  
1.  <span data-ttu-id="70881-120">呼び出し、関数とその引数、引数の型の名前を特定し、値だけでなく、名前とそれを含んでいる DLL の場所を返します。</span><span class="sxs-lookup"><span data-stu-id="70881-120">Determine the name of the function you want to call, plus its arguments, argument types, and return value, as well as the name and location of the DLL that contains it.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="70881-121">Windows Api の詳細については、プラットフォーム SDK の Windows API では、Win32 SDK のマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="70881-121">For complete information about the Windows APIs, see the Win32 SDK documentation in the Platform SDK Windows API.</span></span> <span data-ttu-id="70881-122">Windows Api を使用する定数の詳細については、Windows.h、プラットフォーム SDK に含まれているなどのヘッダー ファイルを調べてください。</span><span class="sxs-lookup"><span data-stu-id="70881-122">For more information about the constants that Windows APIs use, examine the header files such as Windows.h included with the Platform SDK.</span></span>  
  
2.  <span data-ttu-id="70881-123">クリックして新しい Windows アプリケーション プロジェクトを開く**新規**上、**ファイル**メニューをクリックし、**プロジェクト**です。</span><span class="sxs-lookup"><span data-stu-id="70881-123">Open a new Windows Application project by clicking **New** on the **File** menu, and then clicking **Project**.</span></span> <span data-ttu-id="70881-124">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="70881-124">The **New Project** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="70881-125">選択**Windows アプリケーション**の一覧から[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]プロジェクト テンプレート。</span><span class="sxs-lookup"><span data-stu-id="70881-125">Select **Windows Application** from the list of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] project templates.</span></span> <span data-ttu-id="70881-126">新しいプロジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="70881-126">The new project is displayed.</span></span>  
  
4.  <span data-ttu-id="70881-127">次の追加`Declare`関数には、クラスまたはモジュールの DLL を使用します。</span><span class="sxs-lookup"><span data-stu-id="70881-127">Add the following `Declare` function either to the class or module in which you want to use the DLL:</span></span>  
  
     [!code-vb[VbVbalrInterop#9](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_1.vb)]  
  
### <a name="parts-of-the-declare-statement"></a><span data-ttu-id="70881-128">部分、Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="70881-128">Parts of the Declare Statement</span></span>  
 <span data-ttu-id="70881-129">`Declare`ステートメントには、次の要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="70881-129">The `Declare` statement includes the following elements.</span></span>  
  
#### <a name="auto-modifier"></a><span data-ttu-id="70881-130">Auto 修飾子</span><span class="sxs-lookup"><span data-stu-id="70881-130">Auto modifier</span></span>  
 <span data-ttu-id="70881-131">`Auto`修飾子が共通言語ランタイムの規則またはエイリアス名 (指定されている場合) に従って、メソッド名に基づく文字列に変換するランタイムに指示します。</span><span class="sxs-lookup"><span data-stu-id="70881-131">The `Auto` modifier instructs the runtime to convert the string based on the method name according to common language runtime rules (or alias name if specified).</span></span>  
  
#### <a name="lib-and-alias-keywords"></a><span data-ttu-id="70881-132">Lib とエイリアスのキーワード</span><span class="sxs-lookup"><span data-stu-id="70881-132">Lib and Alias keywords</span></span>  
 <span data-ttu-id="70881-133">名前次、`Function`キーワードは、インポートされた関数にアクセスする、プログラムで使用される名前です。</span><span class="sxs-lookup"><span data-stu-id="70881-133">The name following the `Function` keyword is the name your program uses to access the imported function.</span></span> <span data-ttu-id="70881-134">実際の呼び出しには、関数の名前と同じことができます、または任意の有効なプロシージャの名前と、採用を使用することができます、`Alias`の実際の呼び出しには、関数の名前を指定するキーワードです。</span><span class="sxs-lookup"><span data-stu-id="70881-134">It can be the same as the real name of the function you are calling, or you can use any valid procedure name and then employ the `Alias` keyword to specify the real name of the function you are calling.</span></span>  
  
 <span data-ttu-id="70881-135">指定して、`Lib`キーワード、呼び出している関数を含んでいる DLL の場所と名前。</span><span class="sxs-lookup"><span data-stu-id="70881-135">Specify the `Lib` keyword, followed by the name and location of the DLL that contains the function you are calling.</span></span> <span data-ttu-id="70881-136">Windows システム ディレクトリ内にあるファイルのパスを指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="70881-136">You do not need to specify the path for files located in the Windows system directories.</span></span>  
  
 <span data-ttu-id="70881-137">使用して、`Alias`を呼び出している関数の名前が有効な場合は、キーワード[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]プロシージャ名、またはアプリケーション内の他の項目の名前と競合しています。</span><span class="sxs-lookup"><span data-stu-id="70881-137">Use the `Alias` keyword if the name of the function you are calling is not a valid [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] procedure name, or conflicts with the name of other items in your application.</span></span> <span data-ttu-id="70881-138">`Alias`呼び出される関数の場合は true。 名前を示します。</span><span class="sxs-lookup"><span data-stu-id="70881-138">`Alias` indicates the true name of the function being called.</span></span>  
  
#### <a name="argument-and-data-type-declarations"></a><span data-ttu-id="70881-139">引数とデータ型の宣言</span><span class="sxs-lookup"><span data-stu-id="70881-139">Argument and Data Type Declarations</span></span>  
 <span data-ttu-id="70881-140">引数とそのデータ型を宣言します。</span><span class="sxs-lookup"><span data-stu-id="70881-140">Declare the arguments and their data types.</span></span> <span data-ttu-id="70881-141">この部分は、Windows で使用されるデータ型は、Visual Studio のデータ型に対応していないために、難しい課題にすることができます。</span><span class="sxs-lookup"><span data-stu-id="70881-141">This part can be challenging because the data types that Windows uses do not correspond to Visual Studio data types.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="70881-142">作業の多くの役割を互換性のあるデータ型と呼ばれるプロセスの引数を変換することで*マーシャ リング*です。</span><span class="sxs-lookup"><span data-stu-id="70881-142"> does a lot of the work for you by converting arguments to compatible data types, a process called *marshaling*.</span></span> <span data-ttu-id="70881-143">使用して引数をマーシャ リング方法を明示的に制御できる、<xref:System.Runtime.InteropServices.MarshalAsAttribute>属性で定義されている、<xref:System.Runtime.InteropServices>名前空間。</span><span class="sxs-lookup"><span data-stu-id="70881-143">You can explicitly control how arguments are marshaled by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute defined in the <xref:System.Runtime.InteropServices> namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="70881-144">以前のバージョンの[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]パラメーターを宣言することで`As Any`、つまり、すべてのデータのデータ型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="70881-144">Previous versions of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] allowed you to declare parameters `As Any`, meaning that data of any data type could be used.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="70881-145">すべての特定のデータ型を使用する必要があります`Declare`ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="70881-145"> requires that you use a specific data type for all `Declare` statements.</span></span>  
  
#### <a name="windows-api-constants"></a><span data-ttu-id="70881-146">Windows API の定数</span><span class="sxs-lookup"><span data-stu-id="70881-146">Windows API Constants</span></span>  
 <span data-ttu-id="70881-147">いくつかの引数は、定数の組み合わせです。</span><span class="sxs-lookup"><span data-stu-id="70881-147">Some arguments are combinations of constants.</span></span> <span data-ttu-id="70881-148">たとえば、`MessageBox`このチュートリアルで示す API は、という名前の整数引数を受け取る`Typ`メッセージ ボックスを表示する方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="70881-148">For example, the `MessageBox` API shown in this walkthrough accepts an integer argument called `Typ` that controls how the message box is displayed.</span></span> <span data-ttu-id="70881-149">確認するには、これらの定数の数値の値を指定できます、 `#define` WinUser.h ファイル内のステートメント。</span><span class="sxs-lookup"><span data-stu-id="70881-149">You can determine the numeric value of these constants by examining the `#define` statements in the file WinUser.h.</span></span> <span data-ttu-id="70881-150">一般に、数値は 16 進数で示される電卓を使用してそれらを追加し、10 進数に変換することがします。</span><span class="sxs-lookup"><span data-stu-id="70881-150">The numeric values are generally shown in hexadecimal, so you may want to use a calculator to add them and convert to decimal.</span></span> <span data-ttu-id="70881-151">感嘆符スタイルの定数を結合する場合など`MB_ICONEXCLAMATION`0x00000030 し、はい/スタイルなし`MB_YESNO`0x00000004、数値を追加して結果を取得する 0x00000034、または 52 の 10 進数。</span><span class="sxs-lookup"><span data-stu-id="70881-151">For example, if you want to combine the constants for the exclamation style `MB_ICONEXCLAMATION` 0x00000030 and the Yes/No style `MB_YESNO` 0x00000004, you can add the numbers and get a result of 0x00000034, or 52 decimal.</span></span> <span data-ttu-id="70881-152">これらの値をアプリケーションで定数として宣言し、それらを結合することをお勧め、10 進数の結果を直接使用できますを使用して、`Or`演算子。</span><span class="sxs-lookup"><span data-stu-id="70881-152">Although you can use the decimal result directly, it is better to declare these values as constants in your application and combine them using the `Or` operator.</span></span>  
  
###### <a name="to-declare-constants-for-windows-api-calls"></a><span data-ttu-id="70881-153">Windows API の呼び出しのための定数を宣言するには</span><span class="sxs-lookup"><span data-stu-id="70881-153">To declare constants for Windows API calls</span></span>  
  
1.  <span data-ttu-id="70881-154">Windows 関数の呼び出しには、ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="70881-154">Consult the documentation for the Windows function you are calling.</span></span> <span data-ttu-id="70881-155">使用されている定数の名前とこれらの定数の数値を含む .h ファイルの名前を決定します。</span><span class="sxs-lookup"><span data-stu-id="70881-155">Determine the name of the constants it uses and the name of the .h file that contains the numeric values for these constants.</span></span>  
  
2.  <span data-ttu-id="70881-156">メモ帳などのテキスト エディターを使用して、ヘッダー (.h) ファイルの内容を表示しを使用する定数を使用して関連付けられている値を検索します。</span><span class="sxs-lookup"><span data-stu-id="70881-156">Use a text editor, such as Notepad, to view the contents of the header (.h) file, and find the values associated with the constants you are using.</span></span> <span data-ttu-id="70881-157">たとえば、 `MessageBox` API の定数を使用して`MB_ICONQUESTION`をメッセージ ボックスに疑問符 () を表示します。</span><span class="sxs-lookup"><span data-stu-id="70881-157">For example, the `MessageBox` API uses the constant `MB_ICONQUESTION` to show a question mark in the message box.</span></span> <span data-ttu-id="70881-158">定義を`MB_ICONQUESTION`WinUser.h では、次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="70881-158">The definition for `MB_ICONQUESTION` is in WinUser.h and appears as follows:</span></span>  
  
     `#define MB_ICONQUESTION             0x00000020L`  
  
3.  <span data-ttu-id="70881-159">該当するショートカットを追加`Const`ステートメントをクラスまたはモジュールがアプリケーションで使用できるこれらの定数を確認します。</span><span class="sxs-lookup"><span data-stu-id="70881-159">Add equivalent `Const` statements to your class or module to make these constants available to your application.</span></span> <span data-ttu-id="70881-160">例:</span><span class="sxs-lookup"><span data-stu-id="70881-160">For example:</span></span>  
  
     [!code-vb[VbVbalrInterop#11](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_2.vb)]  
  
###### <a name="to-call-the-dll-procedure"></a><span data-ttu-id="70881-161">DLL のプロシージャを呼び出しています</span><span class="sxs-lookup"><span data-stu-id="70881-161">To call the DLL procedure</span></span>  
  
1.  <span data-ttu-id="70881-162">という名前のボタンの追加`Button1`の起動時に、プロジェクトの形式し、すると、そのコードを表示する をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="70881-162">Add a button named `Button1` to the startup form for your project, and then double-click it to view its code.</span></span> <span data-ttu-id="70881-163">ボタンのイベント ハンドラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="70881-163">The event handler for the button is displayed.</span></span>  
  
2.  <span data-ttu-id="70881-164">コードを追加して、`Click`プロシージャを呼び出すし、適切な引数を提供する、追加したボタンのイベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="70881-164">Add code to the `Click` event handler for the button you added, to call the procedure and provide the appropriate arguments:</span></span>  
  
     [!code-vb[VbVbalrInterop#12](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_3.vb)]  
  
3.  <span data-ttu-id="70881-165">F5 キーを押してプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="70881-165">Run the project by pressing F5.</span></span> <span data-ttu-id="70881-166">両方と、メッセージ ボックスが表示**はい**と**いいえ**応答ボタン。</span><span class="sxs-lookup"><span data-stu-id="70881-166">The message box is displayed with both **Yes** and **No** response buttons.</span></span> <span data-ttu-id="70881-167">いずれかをクリックします。</span><span class="sxs-lookup"><span data-stu-id="70881-167">Click either one.</span></span>  
  
#### <a name="data-marshaling"></a><span data-ttu-id="70881-168">データ マーシャ リング</span><span class="sxs-lookup"><span data-stu-id="70881-168">Data Marshaling</span></span>  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="70881-169">自動的に変換パラメーターとが Windows API の呼び出しの戻り値のデータ型できますを使用して、 `MarshalAs` API ものと想定するアンマネージ データ型を明示的に指定する属性。</span><span class="sxs-lookup"><span data-stu-id="70881-169"> automatically converts the data types of parameters and return values for Windows API calls, but you can use the `MarshalAs` attribute to explicitly specify unmanaged data types that an API expects.</span></span> <span data-ttu-id="70881-170">相互運用マーシャ リングの詳細については、次を参照してください。[相互運用マーシャ リング](../../../framework/interop/interop-marshaling.md)です。</span><span class="sxs-lookup"><span data-stu-id="70881-170">For more information about interop marshaling, see [Interop Marshaling](../../../framework/interop/interop-marshaling.md).</span></span>  
  
###### <a name="to-use-declare-and-marshalas-in-an-api-call"></a><span data-ttu-id="70881-171">宣言と MarshalAs API 呼び出しで使用するには</span><span class="sxs-lookup"><span data-stu-id="70881-171">To use Declare and MarshalAs in an API call</span></span>  
  
1.  <span data-ttu-id="70881-172">データ型を引数、呼び出す関数の名前を決定する値を返します。</span><span class="sxs-lookup"><span data-stu-id="70881-172">Determine the name of the function you want to call, plus its arguments, data types, and return value.</span></span>  
  
2.  <span data-ttu-id="70881-173">アクセスを簡素化する、`MarshalAs`属性は、追加、`Imports`クラスまたは次の例のように、モジュールのコードの先頭にステートメント。</span><span class="sxs-lookup"><span data-stu-id="70881-173">To simplify access to the `MarshalAs` attribute, add an `Imports` statement to the top of the code for the class or module, as in the following example:</span></span>  
  
     [!code-vb[VbVbalrInterop#13](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]  
  
3.  <span data-ttu-id="70881-174">クラスまたはモジュールを使用しているし、適用にインポートした関数の関数プロトタイプを追加、`MarshalAs`属性をパラメーターまたは戻り値。</span><span class="sxs-lookup"><span data-stu-id="70881-174">Add a function prototype for the imported function to the class or module you are using, and apply the `MarshalAs` attribute to the parameters or return value.</span></span> <span data-ttu-id="70881-175">次の例では、型を要求する API 呼び出し`void*`としてマーシャ リング`AsAny`:</span><span class="sxs-lookup"><span data-stu-id="70881-175">In the following example, an API call that expects the type `void*` is marshaled as `AsAny`:</span></span>  
  
     [!code-vb[VbVbalrInterop#14](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_5.vb)]  
  
## <a name="api-calls-using-dllimport"></a><span data-ttu-id="70881-176">DllImport を使用して、API 呼び出し</span><span class="sxs-lookup"><span data-stu-id="70881-176">API Calls Using DllImport</span></span>  
 <span data-ttu-id="70881-177">`DllImport`属性がタイプ ライブラリを持たない Dll で関数を呼び出す 2 番目の方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="70881-177">The `DllImport` attribute provides a second way to call functions in DLLs without type libraries.</span></span> <span data-ttu-id="70881-178">`DllImport`使用するとほぼ同等な`Declare`ステートメントが関数を呼び出す方法より詳細に制御を提供します。</span><span class="sxs-lookup"><span data-stu-id="70881-178">`DllImport` is roughly equivalent to using a `Declare` statement but provides more control over how functions are called.</span></span>  
  
 <span data-ttu-id="70881-179">使用することができます`DllImport`ほとんどの Windows API の呼び出しは、共有を参照している限りを呼び出します (とも呼ばれる*静的*) メソッドです。</span><span class="sxs-lookup"><span data-stu-id="70881-179">You can use `DllImport` with most Windows API calls as long as the call refers to a shared (sometimes called *static*) method.</span></span> <span data-ttu-id="70881-180">クラスのインスタンスを必要とするメソッドを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="70881-180">You cannot use methods that require an instance of a class.</span></span> <span data-ttu-id="70881-181">異なり`Declare`ステートメント、`DllImport`呼び出しは使用できません、`MarshalAs`属性。</span><span class="sxs-lookup"><span data-stu-id="70881-181">Unlike `Declare` statements, `DllImport` calls cannot use the `MarshalAs` attribute.</span></span>  
  
#### <a name="to-call-a-windows-api-using-the-dllimport-attribute"></a><span data-ttu-id="70881-182">DllImport 属性を使用して Windows API を呼び出す</span><span class="sxs-lookup"><span data-stu-id="70881-182">To call a Windows API using the DllImport attribute</span></span>  
  
1.  <span data-ttu-id="70881-183">クリックして新しい Windows アプリケーション プロジェクトを開く**新規**上、**ファイル**メニューをクリックし、**プロジェクト**です。</span><span class="sxs-lookup"><span data-stu-id="70881-183">Open a new Windows Application project by clicking **New** on the **File** menu, and then clicking **Project**.</span></span> <span data-ttu-id="70881-184">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="70881-184">The **New Project** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="70881-185">選択**Windows アプリケーション**の一覧から[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]プロジェクト テンプレート。</span><span class="sxs-lookup"><span data-stu-id="70881-185">Select **Windows Application** from the list of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] project templates.</span></span> <span data-ttu-id="70881-186">新しいプロジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="70881-186">The new project is displayed.</span></span>  
  
3.  <span data-ttu-id="70881-187">という名前のボタンの追加`Button2`スタートアップ フォームにします。</span><span class="sxs-lookup"><span data-stu-id="70881-187">Add a button named `Button2` to the startup form.</span></span>  
  
4.  <span data-ttu-id="70881-188">ダブルクリックして`Button2`フォームのコード ビューを開きます。</span><span class="sxs-lookup"><span data-stu-id="70881-188">Double-click `Button2` to open the code view for the form.</span></span>  
  
5.  <span data-ttu-id="70881-189">アクセスを簡単に`DllImport`、追加、`Imports`スタートアップ フォーム クラスのコードの先頭にステートメント。</span><span class="sxs-lookup"><span data-stu-id="70881-189">To simplify access to `DllImport`, add an `Imports` statement to the top of the code for the startup form class:</span></span>  
  
     [!code-vb[VbVbalrInterop#13](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_4.vb)]  
  
6.  <span data-ttu-id="70881-190">空の関数を前の宣言、 `End Class` 、フォーム、名、関数のステートメント`MoveFile`です。</span><span class="sxs-lookup"><span data-stu-id="70881-190">Declare an empty function preceding the `End Class` statement for the form, and name the function `MoveFile`.</span></span>  
  
7.  <span data-ttu-id="70881-191">適用、`Public`と`Shared`関数宣言とパラメーターを設定する修飾子`MoveFile`Windows API 関数を使用して、引数に基づきます。</span><span class="sxs-lookup"><span data-stu-id="70881-191">Apply the `Public` and `Shared` modifiers to the function declaration and set parameters for `MoveFile` based on the arguments the Windows API function uses:</span></span>  
  
     [!code-vb[VbVbalrInterop#16](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_6.vb)]  
  
     <span data-ttu-id="70881-192">関数は、任意の有効なプロシージャ名前を持つことができます。`DllImport`属性は、DLL の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="70881-192">Your function can have any valid procedure name; the `DllImport` attribute specifies the name in the DLL.</span></span> <span data-ttu-id="70881-193">相互運用性は、パラメーターのマーシャ リングも処理やデータに類似する Visual Studio のデータ型を選択できるように、戻り値型 API ではあります。</span><span class="sxs-lookup"><span data-stu-id="70881-193">It also handles interoperability marshaling for the parameters and return values, so you can choose Visual Studio data types that are similar to the data types the API uses.</span></span>  
  
8.  <span data-ttu-id="70881-194">適用、`DllImport`属性を空の関数。</span><span class="sxs-lookup"><span data-stu-id="70881-194">Apply the `DllImport` attribute to the empty function.</span></span> <span data-ttu-id="70881-195">最初のパラメーターを呼び出している関数を含んでいる DLL の場所と名前です。</span><span class="sxs-lookup"><span data-stu-id="70881-195">The first parameter is the name and location of the DLL containing the function you are calling.</span></span> <span data-ttu-id="70881-196">Windows システム ディレクトリ内にあるファイルのパスを指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="70881-196">You do not need to specify the path for files located in the Windows system directories.</span></span> <span data-ttu-id="70881-197">2 番目のパラメーターは、Windows API では、関数の名前を指定する名前付き引数です。</span><span class="sxs-lookup"><span data-stu-id="70881-197">The second parameter is a named argument that specifies the name of the function in the Windows API.</span></span> <span data-ttu-id="70881-198">この例では、`DllImport`属性への呼び出しを強制する`MoveFile`に転送される`MoveFileW`KERNEL32 にします。DLL です。</span><span class="sxs-lookup"><span data-stu-id="70881-198">In this example, the `DllImport` attribute forces calls to `MoveFile` to be forwarded to `MoveFileW` in KERNEL32.DLL.</span></span> <span data-ttu-id="70881-199">`MoveFileW`メソッドは、パスからファイルをコピー`src`パスに`dst`です。</span><span class="sxs-lookup"><span data-stu-id="70881-199">The `MoveFileW` method copies a file from the path `src` to the path `dst`.</span></span>  
  
     [!code-vb[VbVbalrInterop#17](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_7.vb)]  
  
9. <span data-ttu-id="70881-200">コードを追加して、`Button2_Click`イベント ハンドラーで関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="70881-200">Add code to the `Button2_Click` event handler to call the function:</span></span>  
  
     [!code-vb[VbVbalrInterop#18](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-calling-windows-apis_8.vb)]  
  
10. <span data-ttu-id="70881-201">Test.txt という名前のファイルを作成し、ハード ドライブに C:\Tmp ディレクトリに配置します。</span><span class="sxs-lookup"><span data-stu-id="70881-201">Create a file named Test.txt and place it in the C:\Tmp directory on your hard drive.</span></span> <span data-ttu-id="70881-202">必要な場合は、Tmp ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="70881-202">Create the Tmp directory if necessary.</span></span>  
  
11. <span data-ttu-id="70881-203">F5 キーを押してアプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="70881-203">Press F5 to start the application.</span></span> <span data-ttu-id="70881-204">メイン フォームが表示されます。</span><span class="sxs-lookup"><span data-stu-id="70881-204">The main form appears.</span></span>  
  
12. <span data-ttu-id="70881-205">をクリックして**Button2**です。</span><span class="sxs-lookup"><span data-stu-id="70881-205">Click **Button2**.</span></span> <span data-ttu-id="70881-206">ファイルを移動できる場合は、「ファイルが正常に移動されました」メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="70881-206">The message "The file was moved successfully" is displayed if the file can be moved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70881-207">関連項目</span><span class="sxs-lookup"><span data-stu-id="70881-207">See Also</span></span>  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="70881-208">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="70881-208">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="70881-209">Auto</span><span class="sxs-lookup"><span data-stu-id="70881-209">Auto</span></span>](../../../visual-basic/language-reference/modifiers/auto.md)  
 [<span data-ttu-id="70881-210">Alias</span><span class="sxs-lookup"><span data-stu-id="70881-210">Alias</span></span>](../../../visual-basic/language-reference/statements/alias-clause.md)  
 [<span data-ttu-id="70881-211">COM 相互運用</span><span class="sxs-lookup"><span data-stu-id="70881-211">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)  
 [<span data-ttu-id="70881-212">マネージ コードでのプロトタイプの作成</span><span class="sxs-lookup"><span data-stu-id="70881-212">Creating Prototypes in Managed Code</span></span>](../../../framework/interop/creating-prototypes-in-managed-code.md)  
 [<span data-ttu-id="70881-213">コールバック メソッドとしてのデリゲートのマーシャ リング</span><span class="sxs-lookup"><span data-stu-id="70881-213">Marshaling a Delegate as a Callback Method</span></span>](../../../framework/interop/marshaling-a-delegate-as-a-callback-method.md)
