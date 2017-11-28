---
title: "方法: コマンドラインから Windows フォーム アプリケーションを作成します。"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-winforms
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, application development from command line
- Windows Forms, getting started
- Windows Forms, creating basic form
ms.assetid: 45ad3f8b-1c26-4c9f-91a9-3bb0759a47a4
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e6ddb27f724e30071be339ac753cfd85599ccd86
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-windows-forms-application-from-the-command-line"></a><span data-ttu-id="722fb-102">方法: コマンドラインから Windows フォーム アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="722fb-102">How to: Create a Windows Forms application from the command line</span></span>
<span data-ttu-id="722fb-103">次の手順では、コマンドラインから Windows フォーム アプリケーションを作成して実行するために完了する必要のある基本的な手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="722fb-103">The following procedures describe the basic steps that you must complete to create and run a Windows Forms application from the command line.</span></span> <span data-ttu-id="722fb-104">Visual Studio では、これらの手順に対する広範なサポートが用意されています。</span><span class="sxs-lookup"><span data-stu-id="722fb-104">There is extensive support for these procedures in Visual Studio.</span></span>  <span data-ttu-id="722fb-105">参照してください[チュートリアル: 簡単な Windows フォームの作成](http://msdn.microsoft.com/library/z9w2f38k\(v=vs.100\))です。</span><span class="sxs-lookup"><span data-stu-id="722fb-105">Also see [Walkthrough: Creating a Simple Windows Form](http://msdn.microsoft.com/library/z9w2f38k\(v=vs.100\)).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="722fb-106">プロシージャ</span><span class="sxs-lookup"><span data-stu-id="722fb-106">Procedure</span></span>  
  
#### <a name="to-create-the-form"></a><span data-ttu-id="722fb-107">フォームを作成するには</span><span class="sxs-lookup"><span data-stu-id="722fb-107">To create the form</span></span>  
  
1.  <span data-ttu-id="722fb-108">空のコード ファイルに、次の import ステートメントまたは using ステートメントを入力します。</span><span class="sxs-lookup"><span data-stu-id="722fb-108">In an empty code file, type the following import or using statements:</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BasicForm#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#2)]  
  
2.  <span data-ttu-id="722fb-109">フォーム クラスから継承する `Form1` という名前のクラスを宣言します。</span><span class="sxs-lookup"><span data-stu-id="722fb-109">Declare a class named `Form1` that inherits from the Form class.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BasicForm#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#3)]  
  
3.  <span data-ttu-id="722fb-110">`Form1` の既定のコンストラクターを作成します。</span><span class="sxs-lookup"><span data-stu-id="722fb-110">Create a default constructor for `Form1`.</span></span>  
  
     <span data-ttu-id="722fb-111">後続の手順で、コンストラクターにさらにコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="722fb-111">You will add more code to the constructor in a subsequent procedure.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.BasicForm#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#4)]  
  
4.  <span data-ttu-id="722fb-112">`Main` メソッドをクラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="722fb-112">Add a `Main` method to the class.</span></span>  
  
    1.  <span data-ttu-id="722fb-113"><xref:System.STAThreadAttribute> を `Main` メソッドに適用し、Windows フォーム アプリケーションがシングル スレッド アパートメントであることを指定します。</span><span class="sxs-lookup"><span data-stu-id="722fb-113">Apply the <xref:System.STAThreadAttribute> to the `Main` method to specify your Windows Forms application is a single threaded apartment.</span></span>  
  
    2.  <span data-ttu-id="722fb-114"><xref:System.Windows.Forms.Application.EnableVisualStyles%2A> を呼び出して、アプリケーションを Windows XP の外観にします。</span><span class="sxs-lookup"><span data-stu-id="722fb-114">Call <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> to give a Windows XP appearance to your application.</span></span>  
  
    3.  <span data-ttu-id="722fb-115">フォームのインスタンスを作成して実行します。</span><span class="sxs-lookup"><span data-stu-id="722fb-115">Create an instance of the form and run it.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BasicForm#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.BasicForm#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BasicForm/VB/Form1.vb#5)]  
  
#### <a name="to-compile-and-run-the-application"></a><span data-ttu-id="722fb-116">アプリケーションをコンパイルして実行するには</span><span class="sxs-lookup"><span data-stu-id="722fb-116">To compile and run the application</span></span>  
  
1.  <span data-ttu-id="722fb-117">.NET Framework コマンド プロンプトで、`Form1` クラスを作成したディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="722fb-117">At the .NET Framework command prompt, navigate to the directory you created the `Form1` class.</span></span>  
  
2.  <span data-ttu-id="722fb-118">フォームをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="722fb-118">Compile the form.</span></span>  
  
    -   <span data-ttu-id="722fb-119">C# を使用している場合は、次のように入力します。`csc form1.cs`</span><span class="sxs-lookup"><span data-stu-id="722fb-119">If you are using C#, type: `csc form1.cs`</span></span>  
  
         `-or-`  
  
    -   <span data-ttu-id="722fb-120">Visual Basic を使用している場合は、次のように入力します。`vbc form1.vb /r:system.dll,system.drawing.dll,system.windows.forms.dll`</span><span class="sxs-lookup"><span data-stu-id="722fb-120">If you are using Visual Basic, type: `vbc form1.vb /r:system.dll,system.drawing.dll,system.windows.forms.dll`</span></span>  
  
3.  <span data-ttu-id="722fb-121">コマンド プロンプトで次のように入力します。`Form1.exe`</span><span class="sxs-lookup"><span data-stu-id="722fb-121">At the command prompt, type: `Form1.exe`</span></span>  
  
## <a name="adding-a-control-and-handling-an-event"></a><span data-ttu-id="722fb-122">コントロールの追加とイベントの処理</span><span class="sxs-lookup"><span data-stu-id="722fb-122">Adding a Control and Handling an Event</span></span>  
 <span data-ttu-id="722fb-123">前の手順は、コンパイルして実行する基本的な Windows フォームを作成する方法を示しました。</span><span class="sxs-lookup"><span data-stu-id="722fb-123">The previous procedure steps demonstrated how to just create a basic Windows Form that compiles and runs.</span></span> <span data-ttu-id="722fb-124">次の手順では、コントロールを作成してフォームに追加し、コントロールのイベントを処理する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="722fb-124">The next procedure will show you how to create and add a control to the form, and handle an event for the control.</span></span> <span data-ttu-id="722fb-125">Windows フォームに追加できるコントロールの詳細については、次を参照してください。 [Windows フォーム コントロール](../../../docs/framework/winforms/controls/index.md)です。</span><span class="sxs-lookup"><span data-stu-id="722fb-125">For more information about the controls you can add to Windows Forms, see [Windows Forms Controls](../../../docs/framework/winforms/controls/index.md).</span></span>  
  
 <span data-ttu-id="722fb-126">Windows フォーム アプリケーションを作成する方法を理解するだけでなく、イベント ベースのプログラミングとユーザー入力を処理する方法を理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="722fb-126">In addition to understanding how to create Windows Forms applications, you should understand event-based programming and how to handle user input.</span></span> <span data-ttu-id="722fb-127">詳細については、次を参照してください[Windows フォームでのイベント ハンドラーの作成](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)、および[ユーザー入力の処理。](../../../docs/framework/winforms/controls/handling-user-input.md)</span><span class="sxs-lookup"><span data-stu-id="722fb-127">For more information, see [Creating Event Handlers in Windows Forms](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md), and [Handling User Input](../../../docs/framework/winforms/controls/handling-user-input.md)</span></span>  
  
#### <a name="to-declare-a-button-control-and-handle-its-click-event"></a><span data-ttu-id="722fb-128">ボタン コントロールを宣言して、クリック イベントを処理するには</span><span class="sxs-lookup"><span data-stu-id="722fb-128">To declare a button control and handle its click event</span></span>  
  
1.  <span data-ttu-id="722fb-129">`button1` という名前のボタン コントロールを宣言します。</span><span class="sxs-lookup"><span data-stu-id="722fb-129">Declare a button control named `button1`.</span></span>  
  
2.  <span data-ttu-id="722fb-130">コンストラクターでボタンを作成し、<xref:System.Windows.Forms.Control.Size%2A>、<xref:System.Windows.Forms.Control.Location%2A>、および <xref:System.Windows.Forms.Control.Text%2A> の各プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="722fb-130">In the constructor, create the button and set its <xref:System.Windows.Forms.Control.Size%2A>, <xref:System.Windows.Forms.Control.Location%2A> and <xref:System.Windows.Forms.Control.Text%2A> properties.</span></span>  
  
3.  <span data-ttu-id="722fb-131">フォームにボタンを追加します。</span><span class="sxs-lookup"><span data-stu-id="722fb-131">Add the button to the form.</span></span>  
  
     <span data-ttu-id="722fb-132">次のコード例は、ボタン コントロールを宣言する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="722fb-132">The following code example demonstrates how to declare the button control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.FormWithButton#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#2)]  
  
4.  <span data-ttu-id="722fb-133">ボタンで <xref:System.Windows.Forms.Control.Click> イベントを処理するメソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="722fb-133">Create a method to handle the <xref:System.Windows.Forms.Control.Click> event for the button.</span></span>  
  
5.  <span data-ttu-id="722fb-134">クリック イベント ハンドラーで、メッセージ "Hello World" と共に <xref:System.Windows.Forms.MessageBox> を表示します。</span><span class="sxs-lookup"><span data-stu-id="722fb-134">In the click event handler, display a <xref:System.Windows.Forms.MessageBox> with the message, "Hello World".</span></span>  
  
     <span data-ttu-id="722fb-135">次のコード例は、ボタン コントロールのクリック イベントを処理する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="722fb-135">The following code example demonstrates how to handle the button control's click event.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.FormWithButton#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#3)]  
  
6.  <span data-ttu-id="722fb-136"><xref:System.Windows.Forms.Control.Click> イベントを作成したメソッドに関連付けます。</span><span class="sxs-lookup"><span data-stu-id="722fb-136">Associate the <xref:System.Windows.Forms.Control.Click> event with the method you created.</span></span>  
  
     <span data-ttu-id="722fb-137">次のコード例は、イベントをメソッドに関連付ける方法を示します。</span><span class="sxs-lookup"><span data-stu-id="722fb-137">The following code example demonstrates how to associate the event with the method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.FormWithButton#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.FormWithButton#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#4)]  
  
7.  <span data-ttu-id="722fb-138">前の手順で説明したように、アプリケーションをコンパイルして実行します。</span><span class="sxs-lookup"><span data-stu-id="722fb-138">Compile and run the application as described in the previous procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="722fb-139">例</span><span class="sxs-lookup"><span data-stu-id="722fb-139">Example</span></span>  
 <span data-ttu-id="722fb-140">次のコード例は、前の手順の完全な例です。</span><span class="sxs-lookup"><span data-stu-id="722fb-140">Following code example is the complete example from the previous procedures.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FormWithButton#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.FormWithButton#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FormWithButton/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="722fb-141">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="722fb-141">Compiling the Code</span></span>  
  
-   <span data-ttu-id="722fb-142">コードをコンパイルするには、アプリケーションをコンパイルして実行する方法を説明した、前述の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="722fb-142">To compile the code, follow the instructions in the proceeding procedure that describe how to compile and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="722fb-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="722fb-143">See Also</span></span>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.Windows.Forms.Control>  
 [<span data-ttu-id="722fb-144">Windows フォームの表示形式の変更</span><span class="sxs-lookup"><span data-stu-id="722fb-144">Changing the Appearance of Windows Forms</span></span>](../../../docs/framework/winforms/changing-the-appearance-of-windows-forms.md)  
 [<span data-ttu-id="722fb-145">Windows フォーム アプリケーションの拡張</span><span class="sxs-lookup"><span data-stu-id="722fb-145">Enhancing Windows Forms Applications</span></span>](../../../docs/framework/winforms/advanced/index.md)  
 [<span data-ttu-id="722fb-146">Windows フォームについて</span><span class="sxs-lookup"><span data-stu-id="722fb-146">Getting Started with Windows Forms</span></span>](../../../docs/framework/winforms/getting-started-with-windows-forms.md)
