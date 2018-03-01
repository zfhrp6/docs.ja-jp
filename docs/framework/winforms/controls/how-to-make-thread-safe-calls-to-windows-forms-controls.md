---
title: "方法 : Windows フォーム コントロールのスレッド セーフな呼び出しを行う"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- EHInvalidOperation.WinForms.IllegalCrossThreadCall
helpviewer_keywords:
- thread safety [Windows Forms], calling controls [Windows Forms]
- calling controls [Windows Forms], thread safety [Windows Forms]
- CheckForIllegalCrossThreadCalls property [Windows Forms]
- Windows Forms controls [Windows Forms], multithreading
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], cross-thread calls
- controls [Windows Forms], multithreading
ms.assetid: 138f38b6-1099-4fd5-910c-390b41cbad35
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7cca363be57e5c5022c70c62d876f62cebc6e9c0
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a><span data-ttu-id="d18c2-102">方法 : Windows フォーム コントロールのスレッド セーフな呼び出しを行う</span><span class="sxs-lookup"><span data-stu-id="d18c2-102">How to: Make Thread-Safe Calls to Windows Forms Controls</span></span>
<span data-ttu-id="d18c2-103">マルチスレッドを使用して Windows フォーム アプリケーションのパフォーマンスを向上させる場合は、必ずスレッド セーフな方法でコントロールを呼び出してください。</span><span class="sxs-lookup"><span data-stu-id="d18c2-103">If you use multithreading to improve the performance of your Windows Forms applications, you must make sure that you make calls to your controls in a thread-safe way.</span></span>  
  
 <span data-ttu-id="d18c2-104">Windows フォーム コントロールへのアクセスは、本質的にスレッド セーフではありません。</span><span class="sxs-lookup"><span data-stu-id="d18c2-104">Access to Windows Forms controls is not inherently thread safe.</span></span> <span data-ttu-id="d18c2-105">コントロールの状態を操作するスレッドが複数ある場合、コントロールが不整合な状態になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d18c2-105">If you have two or more threads manipulating the state of a control, it is possible to force the control into an inconsistent state.</span></span> <span data-ttu-id="d18c2-106">競合状態やデッドロックなど、他のスレッド関連のバグが生じる可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="d18c2-106">Other thread-related bugs are possible, such as race conditions and deadlocks.</span></span> <span data-ttu-id="d18c2-107">コントロールへのアクセスがスレッド セーフな方法で実行されることを確認することが重要です。</span><span class="sxs-lookup"><span data-stu-id="d18c2-107">It is important to make sure that access to your controls is performed in a thread-safe way.</span></span>  
  
 <span data-ttu-id="d18c2-108"><xref:System.Windows.Forms.Control.Invoke%2A> メソッドを使用せずにコントロールを作成したスレッド以外のスレッドからコントロールを呼び出すのは安全ではありません。</span><span class="sxs-lookup"><span data-stu-id="d18c2-108">It is unsafe to call a control from a thread other than the one that created the control without using the <xref:System.Windows.Forms.Control.Invoke%2A> method.</span></span> <span data-ttu-id="d18c2-109">スレッド セーフでない呼び出しの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d18c2-109">The following is an example of a call that is not thread safe.</span></span>  
  
```csharp  
// This event handler creates a thread that calls a   
// Windows Forms control in an unsafe way.  
private void setTextUnsafeBtn_Click(  
    object sender,   
    EventArgs e)  
{  
    this.demoThread =   
        new Thread(new ThreadStart(this.ThreadProcUnsafe));  
  
    this.demoThread.Start();  
}  
  
// This method is executed on the worker thread and makes  
// an unsafe call on the TextBox control.  
private void ThreadProcUnsafe()  
{  
    this.textBox1.Text = "This text was set unsafely.";  
}  
```  
  
```vb  
' This event handler creates a thread that calls a   
' Windows Forms control in an unsafe way.  
 Private Sub setTextUnsafeBtn_Click( _  
 ByVal sender As Object, _  
 ByVal e As EventArgs) Handles setTextUnsafeBtn.Click  
  
     Me.demoThread = New Thread( _  
     New ThreadStart(AddressOf Me.ThreadProcUnsafe))  
  
     Me.demoThread.Start()  
 End Sub  
  
' This method is executed on the worker thread and makes  
' an unsafe call on the TextBox control.  
Private Sub ThreadProcUnsafe()  
   Me.textBox1.Text = "This text was set unsafely."  
End Sub  
```  
  
```cpp  
// This event handler creates a thread that calls a  
    // Windows Forms control in an unsafe way.  
private:  
    void setTextUnsafeBtn_Click(Object^ sender, EventArgs^ e)  
    {  
        this->demoThread =  
            gcnew Thread(gcnew ThreadStart(this,&Form1::ThreadProcUnsafe));  
  
        this->demoThread->Start();  
    }  
  
    // This method is executed on the worker thread and makes  
    // an unsafe call on the TextBox control.  
private:  
    void ThreadProcUnsafe()  
    {  
        this->textBox1->Text = "This text was set unsafely.";  
    }  
```  
  
 <span data-ttu-id="d18c2-110">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] は、スレッド セーフでない方法でコントロールにアクセスしていることを検出するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="d18c2-110">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] helps you detect when you are accessing your controls in a manner that is not thread safe.</span></span> <span data-ttu-id="d18c2-111">デバッガーでアプリケーションを実行しているときに、コントロールを作成したスレッド以外のスレッドがそのコントロールを呼び出そうとすると、デバッガーは <xref:System.InvalidOperationException> を発生させ、"コントロールが作成されたスレッド以外のスレッドからコントロール ' *コントロール名* ' がアクセスされました。" というメッセージが示されます。</span><span class="sxs-lookup"><span data-stu-id="d18c2-111">When you are running your application in the debugger, and a thread other than the one which created a control tries to call that control, the debugger raises an <xref:System.InvalidOperationException> with the message, "Control *control name* accessed from a thread other than the thread it was created on."</span></span>  
  
 <span data-ttu-id="d18c2-112">この例外は、デバッグ時には確実に発生しますが、場合によっては実行時に発生することもあります。</span><span class="sxs-lookup"><span data-stu-id="d18c2-112">This exception occurs reliably during debugging and, under some circumstances, at run time.</span></span> <span data-ttu-id="d18c2-113">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] より前に [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] を使用して、作成したアプリケーションのデバッグを行う場合に、この例外が発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="d18c2-113">You might see this exception when you debug applications that you wrote with the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] prior to the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span> <span data-ttu-id="d18c2-114">この問題が発生したら修正することを強くお勧めしますが、 <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A> プロパティを `false`に設定して無効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="d18c2-114">You are strongly advised to fix this problem when you see it, but you can disable it by setting the <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A> property to `false`.</span></span> <span data-ttu-id="d18c2-115">これによりコントロールは、Visual Studio .NET 2003 および [!INCLUDE[net_v11_short](../../../../includes/net-v11-short-md.md)]の下で実行しているかのように実行されます。</span><span class="sxs-lookup"><span data-stu-id="d18c2-115">This causes your control to run like it would run under Visual Studio .NET 2003 and the [!INCLUDE[net_v11_short](../../../../includes/net-v11-short-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d18c2-116">フォームで ActiveX コントロールを使用している場合、デバッガー下で実行すると、スレッド間の <xref:System.InvalidOperationException> を受け取ることがあります。</span><span class="sxs-lookup"><span data-stu-id="d18c2-116">If you are using ActiveX controls on a form, you may receive the cross-thread <xref:System.InvalidOperationException> when you run under the debugger.</span></span> <span data-ttu-id="d18c2-117">これが発生した場合、ActiveX コントロールではマルチスレッドをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="d18c2-117">When this occurs, the ActiveX control does not support multithreading.</span></span> <span data-ttu-id="d18c2-118">Windows フォームでの ActiveX コントロールの使用の詳細については、「 [Windows Forms and Unmanaged Applications](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d18c2-118">For more information about using ActiveX controls with Windows Forms, see [Windows Forms and Unmanaged Applications](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md).</span></span> <span data-ttu-id="d18c2-119">Visual Studio を使用している場合、Visual Studio ホスティング プロセスを無効にすることで、この例外を防止できます。「 [How to: Disable the Hosting Process](/visualstudio/ide/how-to-disable-the-hosting-process)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d18c2-119">If you are using Visual Studio, you can prevent this exception by disabling the Visual Studio hosting process, see [How to: Disable the Hosting Process](/visualstudio/ide/how-to-disable-the-hosting-process).</span></span>  
  
## <a name="making-thread-safe-calls-to-windows-forms-controls"></a><span data-ttu-id="d18c2-120">Windows フォーム コントロールのスレッド セーフな呼び出し</span><span class="sxs-lookup"><span data-stu-id="d18c2-120">Making Thread-Safe Calls to Windows Forms Controls</span></span>  
  
#### <a name="to-make-a-thread-safe-call-to-a-windows-forms-control"></a><span data-ttu-id="d18c2-121">Windows フォーム コントロールのスレッド セーフな呼び出しを行うには</span><span class="sxs-lookup"><span data-stu-id="d18c2-121">To make a thread-safe call to a Windows Forms control</span></span>  
  
1.  <span data-ttu-id="d18c2-122">コントロールの <xref:System.Windows.Forms.Control.InvokeRequired%2A> プロパティを照会します。</span><span class="sxs-lookup"><span data-stu-id="d18c2-122">Query the control's <xref:System.Windows.Forms.Control.InvokeRequired%2A> property.</span></span>  
  
2.  <span data-ttu-id="d18c2-123"><xref:System.Windows.Forms.Control.InvokeRequired%2A> から `true`が返された場合は、デリゲートを使用して <xref:System.Windows.Forms.Control.Invoke%2A> を呼び出します。このデリゲートがコントロールへの実際の呼び出しを行います。</span><span class="sxs-lookup"><span data-stu-id="d18c2-123">If <xref:System.Windows.Forms.Control.InvokeRequired%2A> returns `true`, call <xref:System.Windows.Forms.Control.Invoke%2A> with a delegate that makes the actual call to the control.</span></span>  
  
3.  <span data-ttu-id="d18c2-124"><xref:System.Windows.Forms.Control.InvokeRequired%2A> から `false`が返された場合は、コントロールを直接呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d18c2-124">If <xref:System.Windows.Forms.Control.InvokeRequired%2A> returns `false`, call the control directly.</span></span>  
  
 <span data-ttu-id="d18c2-125">次のコード例では、スレッド セーフな呼び出しが `ThreadProcSafe` メソッドに実装されており、バックグラウンド スレッドによって実行されます。</span><span class="sxs-lookup"><span data-stu-id="d18c2-125">In the following code example, a thread-safe call is implemented in the `ThreadProcSafe` method, which is executed by the background thread.</span></span> <span data-ttu-id="d18c2-126"><xref:System.Windows.Forms.TextBox> コントロールの <xref:System.Windows.Forms.Control.InvokeRequired%2A> から `true`が返された場合、 `ThreadProcSafe` メソッドによって `StringArgReturningVoidDelegate` のインスタンスが作成され、それがフォームの <xref:System.Windows.Forms.Control.Invoke%2A> メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="d18c2-126">If the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.Control.InvokeRequired%2A> returns `true`, the `ThreadProcSafe` method creates an instance of `StringArgReturningVoidDelegate` and passes that to the form's <xref:System.Windows.Forms.Control.Invoke%2A> method.</span></span> <span data-ttu-id="d18c2-127">これにより、 `SetText` メソッドが <xref:System.Windows.Forms.TextBox> コントロールを作成したスレッドで呼び出されます。また、このスレッド コンテキストで、 <xref:System.Windows.Forms.Control.Text%2A> プロパティが直接設定されます。</span><span class="sxs-lookup"><span data-stu-id="d18c2-127">This causes the `SetText` method to be called on the thread that created the <xref:System.Windows.Forms.TextBox> control, and in this thread context the <xref:System.Windows.Forms.Control.Text%2A> property is set directly.</span></span>  
  
```csharp  
// This event handler creates a thread that calls a   
// Windows Forms control in a thread-safe way.  
private void setTextSafeBtn_Click(  
    object sender,   
    EventArgs e)  
{  
    this.demoThread =   
        new Thread(new ThreadStart(this.ThreadProcSafe));  
  
    this.demoThread.Start();  
}  
  
// This method is executed on the worker thread and makes  
// a thread-safe call on the TextBox control.  
private void ThreadProcSafe()  
{  
    this.SetText("This text was set safely.");  
}  
```  
  
```vb  
' This event handler creates a thread that calls a   
' Windows Forms control in a thread-safe way.  
 Private Sub setTextSafeBtn_Click( _  
 ByVal sender As Object, _  
 ByVal e As EventArgs) Handles setTextSafeBtn.Click  
  
     Me.demoThread = New Thread( _  
     New ThreadStart(AddressOf Me.ThreadProcSafe))  
  
     Me.demoThread.Start()  
 End Sub  
  
' This method is executed on the worker thread and makes  
' a thread-safe call on the TextBox control.  
Private Sub ThreadProcSafe()  
   Me.SetText("This text was set safely.")  
 End Sub  
```  
  
```cpp  
// This event handler creates a thread that calls a  
    // Windows Forms control in a thread-safe way.  
private:  
    void setTextSafeBtn_Click(Object^ sender, EventArgs^ e)  
    {  
        this->demoThread =  
            gcnew Thread(gcnew ThreadStart(this,&Form1::ThreadProcSafe));  
  
        this->demoThread->Start();  
    }  
  
    // This method is executed on the worker thread and makes  
    // a thread-safe call on the TextBox control.  
private:  
    void ThreadProcSafe()  
    {  
        this->SetText("This text was set safely.");  
    }  
```  
  
```csharp  
// This delegate enables asynchronous calls for setting  
// the text property on a TextBox control.  
delegate void StringArgReturningVoidDelegate(string text);  
```  
  
```vb  
' This delegate enables asynchronous calls for setting  
' the text property on a TextBox control.  
Delegate Sub StringArgReturningVoidDelegate([text] As String)  
```  
  
```cpp  
// This delegate enables asynchronous calls for setting  
// the text property on a TextBox control.  
delegate void StringArgReturningVoidDelegate(String^ text);  
```  
  
```csharp  
// This method demonstrates a pattern for making thread-safe  
// calls on a Windows Forms control.   
//  
// If the calling thread is different from the thread that  
// created the TextBox control, this method creates a  
// StringArgReturningVoidDelegate and calls itself asynchronously using the  
// Invoke method.  
//  
// If the calling thread is the same as the thread that created  
// the TextBox control, the Text property is set directly.   
  
private void SetText(string text)  
{  
    // InvokeRequired required compares the thread ID of the  
    // calling thread to the thread ID of the creating thread.  
    // If these threads are different, it returns true.  
    if (this.textBox1.InvokeRequired)  
    {     
        StringArgReturningVoidDelegate d = new StringArgReturningVoidDelegate(SetText);  
        this.Invoke(d, new object[] { text });  
    }  
    else  
    {  
        this.textBox1.Text = text;  
    }  
}  
```  
  
```vb  
' This method demonstrates a pattern for making thread-safe  
' calls on a Windows Forms control.   
'  
' If the calling thread is different from the thread that  
' created the TextBox control, this method creates a  
' StringArgReturningVoidDelegate and calls itself asynchronously using the  
' Invoke method.  
'  
' If the calling thread is the same as the thread that created  
 ' the TextBox control, the Text property is set directly.  
  
 Private Sub SetText(ByVal [text] As String)  
  
     ' InvokeRequired required compares the thread ID of the  
     ' calling thread to the thread ID of the creating thread.  
     ' If these threads are different, it returns true.  
     If Me.textBox1.InvokeRequired Then  
         Dim d As New StringArgReturningVoidDelegate(AddressOf SetText)  
         Me.Invoke(d, New Object() {[text]})  
     Else  
         Me.textBox1.Text = [text]  
     End If  
 End Sub  
```  
  
```cpp  
// This method demonstrates a pattern for making thread-safe  
    // calls on a Windows Forms control.  
    //  
    // If the calling thread is different from the thread that  
    // created the TextBox control, this method creates a  
    // StringArgReturningVoidDelegate and calls itself asynchronously using the  
    // Invoke method.  
    //  
    // If the calling thread is the same as the thread that created  
    // the TextBox control, the Text property is set directly.  
  
private:  
    void SetText(String^ text)  
    {  
        // InvokeRequired required compares the thread ID of the  
        // calling thread to the thread ID of the creating thread.  
        // If these threads are different, it returns true.  
        if (this->textBox1->InvokeRequired)  
        {  
            StringArgReturningVoidDelegate^ d =   
                gcnew StringArgReturningVoidDelegate(this, &Form1::SetText);  
            this->Invoke(d, gcnew array<Object^> { text });  
        }  
        else  
        {  
            this->textBox1->Text = text;  
        }  
    }  
```  
  
## <a name="making-thread-safe-calls-by-using-backgroundworker"></a><span data-ttu-id="d18c2-128">BackgroundWorker を使用したスレッド セーフな呼び出し</span><span class="sxs-lookup"><span data-stu-id="d18c2-128">Making Thread-Safe Calls by using BackgroundWorker</span></span>  
 <span data-ttu-id="d18c2-129">アプリケーションにマルチスレッドを実装する場合は、 <xref:System.ComponentModel.BackgroundWorker> コンポーネントを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d18c2-129">The preferred way to implement multithreading in your application is to use the <xref:System.ComponentModel.BackgroundWorker> component.</span></span> <span data-ttu-id="d18c2-130"><xref:System.ComponentModel.BackgroundWorker> コンポーネントでは、マルチスレッドにイベント ドリブン モデルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="d18c2-130">The <xref:System.ComponentModel.BackgroundWorker> component uses an event-driven model for multithreading.</span></span> <span data-ttu-id="d18c2-131">バックグラウンド スレッドが <xref:System.ComponentModel.BackgroundWorker.DoWork> イベント ハンドラーを実行し、コントロールを作成したスレッドが <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> イベント ハンドラーと <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> イベント ハンドラーを実行します。</span><span class="sxs-lookup"><span data-stu-id="d18c2-131">The background thread runs your <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler, and the thread that creates your controls runs your <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> and <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handlers.</span></span> <span data-ttu-id="d18c2-132"><xref:System.ComponentModel.BackgroundWorker.ProgressChanged> イベント ハンドラーと <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> イベント ハンドラーからコントロールを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="d18c2-132">You can call your controls from your <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> and <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handlers.</span></span>  
  
#### <a name="to-make-thread-safe-calls-by-using-backgroundworker"></a><span data-ttu-id="d18c2-133">BackgroundWorker を使用してスレッド セーフな呼び出しを行うには</span><span class="sxs-lookup"><span data-stu-id="d18c2-133">To make thread-safe calls by using BackgroundWorker</span></span>  
  
1.  <span data-ttu-id="d18c2-134">バックグラウンド スレッドで行われるようにする作業を実行するメソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="d18c2-134">Create a method to do the work that you want done in the background thread.</span></span> <span data-ttu-id="d18c2-135">このメソッドで、メイン メソッドにより作成されたコントロールは呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="d18c2-135">Do not call controls created by the main thread in this method.</span></span>  
  
2.  <span data-ttu-id="d18c2-136">バックグラウンド作業の終了後にその結果を報告するメソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="d18c2-136">Create a method to report the results of your background work after it finishes.</span></span> <span data-ttu-id="d18c2-137">このメソッドではメイン スレッドにより作成されたコントロールを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="d18c2-137">You can call controls created by the main thread in this method.</span></span>  
  
3.  <span data-ttu-id="d18c2-138">手順 1 で作成したメソッドを <xref:System.ComponentModel.BackgroundWorker.DoWork> のインスタンスの <xref:System.ComponentModel.BackgroundWorker>イベントにバインドし、手順 2 で作成したメソッドを同じインスタンスの <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> イベントにバインドします。</span><span class="sxs-lookup"><span data-stu-id="d18c2-138">Bind the method created in step 1 to the <xref:System.ComponentModel.BackgroundWorker.DoWork> event of an instance of <xref:System.ComponentModel.BackgroundWorker>, and bind the method created in step 2 to the same instance’s <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event.</span></span>  
  
4.  <span data-ttu-id="d18c2-139">バックグラウンド スレッドを開始するには、 <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> インスタンスの <xref:System.ComponentModel.BackgroundWorker> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d18c2-139">To start the background thread, call the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method of the <xref:System.ComponentModel.BackgroundWorker> instance.</span></span>  
  
 <span data-ttu-id="d18c2-140">次のコード例では、 <xref:System.ComponentModel.BackgroundWorker.DoWork> イベント ハンドラーが <xref:System.Threading.Thread.Sleep%2A> を使用して時間のかかる作業をシミュレートします。</span><span class="sxs-lookup"><span data-stu-id="d18c2-140">In the following code example, the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler uses <xref:System.Threading.Thread.Sleep%2A> to simulate work that takes some time.</span></span> <span data-ttu-id="d18c2-141">フォームの <xref:System.Windows.Forms.TextBox> コントロールは呼び出しません。</span><span class="sxs-lookup"><span data-stu-id="d18c2-141">It does not call the form’s <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="d18c2-142"><xref:System.Windows.Forms.TextBox> コントロールの <xref:System.Windows.Forms.Control.Text%2A> プロパティは <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> イベント ハンドラーで直接設定されます。</span><span class="sxs-lookup"><span data-stu-id="d18c2-142">The <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.Control.Text%2A> property is set directly in the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler.</span></span>  
  
```csharp  
// This BackgroundWorker is used to demonstrate the   
// preferred way of performing asynchronous operations.  
private BackgroundWorker backgroundWorker1;  
```  
  
```vb  
' This BackgroundWorker is used to demonstrate the   
' preferred way of performing asynchronous operations.  
Private WithEvents backgroundWorker1 As BackgroundWorker  
```  
  
```cpp  
// This BackgroundWorker is used to demonstrate the  
    // preferred way of performing asynchronous operations.  
private:  
    BackgroundWorker^ backgroundWorker1;  
```  
  
```csharp  
// This event handler starts the form's   
// BackgroundWorker by calling RunWorkerAsync.  
//  
// The Text property of the TextBox control is set  
// when the BackgroundWorker raises the RunWorkerCompleted  
// event.  
private void setTextBackgroundWorkerBtn_Click(  
    object sender,   
    EventArgs e)  
{  
    this.backgroundWorker1.RunWorkerAsync();  
}  
  
// This event handler sets the Text property of the TextBox  
// control. It is called on the thread that created the   
// TextBox control, so the call is thread-safe.  
//  
// BackgroundWorker is the preferred way to perform asynchronous  
// operations.  
  
private void backgroundWorker1_RunWorkerCompleted(  
    object sender,   
    RunWorkerCompletedEventArgs e)  
{  
    this.textBox1.Text =   
        "This text was set safely by BackgroundWorker.";  
}  
```  
  
```vb  
' This event handler starts the form's   
' BackgroundWorker by calling RunWorkerAsync.  
'  
' The Text property of the TextBox control is set  
' when the BackgroundWorker raises the RunWorkerCompleted  
' event.  
 Private Sub setTextBackgroundWorkerBtn_Click( _  
 ByVal sender As Object, _  
 ByVal e As EventArgs) Handles setTextBackgroundWorkerBtn.Click  
     Me.backgroundWorker1.RunWorkerAsync()  
 End Sub  
  
' This event handler sets the Text property of the TextBox  
' control. It is called on the thread that created the   
' TextBox control, so the call is thread-safe.  
'  
' BackgroundWorker is the preferred way to perform asynchronous  
' operations.  
 Private Sub backgroundWorker1_RunWorkerCompleted( _  
 ByVal sender As Object, _  
 ByVal e As RunWorkerCompletedEventArgs) _  
 Handles backgroundWorker1.RunWorkerCompleted  
     Me.textBox1.Text = _  
     "This text was set safely by BackgroundWorker."  
 End Sub  
```  
  
```cpp  
// This event handler starts the form's  
    // BackgroundWorker by calling RunWorkerAsync.  
    //  
    // The Text property of the TextBox control is set  
    // when the BackgroundWorker raises the RunWorkerCompleted  
    // event.  
private:  
    void setTextBackgroundWorkerBtn_Click(Object^ sender, EventArgs^ e)  
    {  
        this->backgroundWorker1->RunWorkerAsync();  
    }  
  
    // This event handler sets the Text property of the TextBox  
    // control. It is called on the thread that created the  
    // TextBox control, so the call is thread-safe.  
    //  
    // BackgroundWorker is the preferred way to perform asynchronous  
    // operations.  
  
private:  
    void backgroundWorker1_RunWorkerCompleted(  
        Object^ sender,  
        RunWorkerCompletedEventArgs^ e)  
    {  
        this->textBox1->Text =  
            "This text was set safely by BackgroundWorker.";  
    }  
```  
  
 <span data-ttu-id="d18c2-143"><xref:System.ComponentModel.BackgroundWorker.ProgressChanged> イベントを使用して、バックグラウンド タスクの進行状況を報告することもできます。</span><span class="sxs-lookup"><span data-stu-id="d18c2-143">You can also report the progress of a background task by using the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event.</span></span> <span data-ttu-id="d18c2-144">そのイベントを組み込む例については、「 <xref:System.ComponentModel.BackgroundWorker>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d18c2-144">For an example that incorporates that event, see <xref:System.ComponentModel.BackgroundWorker>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d18c2-145">例</span><span class="sxs-lookup"><span data-stu-id="d18c2-145">Example</span></span>  
 <span data-ttu-id="d18c2-146">次のコード例は、3 つのボタンと 1 つのテキスト ボックスを持つフォームで構成される、完全な Windows フォーム アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="d18c2-146">The following code example is a complete Windows Forms application that consists of a form with three buttons and one text box.</span></span> <span data-ttu-id="d18c2-147">最初のボタンは安全でないスレッド間アクセスを示し、2 番目のボタンは <xref:System.Windows.Forms.Control.Invoke%2A>を使用した安全なアクセスを示し、3 番目のボタンは <xref:System.ComponentModel.BackgroundWorker>を使用した安全なアクセスを示します。</span><span class="sxs-lookup"><span data-stu-id="d18c2-147">The first button demonstrates unsafe cross-thread access, the second button demonstrates safe access by using <xref:System.Windows.Forms.Control.Invoke%2A>, and the third button demonstrates safe access by using <xref:System.ComponentModel.BackgroundWorker>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d18c2-148">例を実行する方法の手順は「[方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/cc447f7e-4c3b-4397-9d05-aeba3ca49416)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d18c2-148">For instructions on how to run the example, see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/cc447f7e-4c3b-4397-9d05-aeba3ca49416).</span></span> <span data-ttu-id="d18c2-149">この例では、System.Drawing アセンブリと System.Windows.Forms アセンブリへの参照が必要です。</span><span class="sxs-lookup"><span data-stu-id="d18c2-149">This example requires references to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
```csharp  
using System;  
using System.ComponentModel;  
using System.Threading;  
using System.Windows.Forms;  
  
namespace CrossThreadDemo  
{  
    public class Form1 : Form  
    {  
        // This delegate enables asynchronous calls for setting  
        // the text property on a TextBox control.  
        delegate void StringArgReturningVoidDelegate(string text);  
  
        // This thread is used to demonstrate both thread-safe and  
        // unsafe ways to call a Windows Forms control.  
        private Thread demoThread = null;  
  
        // This BackgroundWorker is used to demonstrate the   
        // preferred way of performing asynchronous operations.  
        private BackgroundWorker backgroundWorker1;  
  
        private TextBox textBox1;  
        private Button setTextUnsafeBtn;  
        private Button setTextSafeBtn;  
        private Button setTextBackgroundWorkerBtn;  
  
        private System.ComponentModel.IContainer components = null;  
  
        public Form1()  
        {  
            InitializeComponent();  
        }  
  
        protected override void Dispose(bool disposing)  
        {  
            if (disposing && (components != null))  
            {  
                components.Dispose();  
            }  
            base.Dispose(disposing);  
        }  
  
        // This event handler creates a thread that calls a   
        // Windows Forms control in an unsafe way.  
        private void setTextUnsafeBtn_Click(  
            object sender,   
            EventArgs e)  
        {  
            this.demoThread =   
                new Thread(new ThreadStart(this.ThreadProcUnsafe));  
  
            this.demoThread.Start();  
        }  
  
        // This method is executed on the worker thread and makes  
        // an unsafe call on the TextBox control.  
        private void ThreadProcUnsafe()  
        {  
            this.textBox1.Text = "This text was set unsafely.";  
        }  
  
        // This event handler creates a thread that calls a   
        // Windows Forms control in a thread-safe way.  
        private void setTextSafeBtn_Click(  
            object sender,   
            EventArgs e)  
        {  
            this.demoThread =   
                new Thread(new ThreadStart(this.ThreadProcSafe));  
  
            this.demoThread.Start();  
        }  
  
        // This method is executed on the worker thread and makes  
        // a thread-safe call on the TextBox control.  
        private void ThreadProcSafe()  
        {  
            this.SetText("This text was set safely.");  
        }  
  
        // This method demonstrates a pattern for making thread-safe  
        // calls on a Windows Forms control.   
        //  
        // If the calling thread is different from the thread that  
        // created the TextBox control, this method creates a  
        // StringArgReturningVoidDelegate and calls itself asynchronously using the  
        // Invoke method.  
        //  
        // If the calling thread is the same as the thread that created  
        // the TextBox control, the Text property is set directly.   
  
        private void SetText(string text)  
        {  
            // InvokeRequired required compares the thread ID of the  
            // calling thread to the thread ID of the creating thread.  
            // If these threads are different, it returns true.  
            if (this.textBox1.InvokeRequired)  
            {     
                StringArgReturningVoidDelegate d = new StringArgReturningVoidDelegate(SetText);  
                this.Invoke(d, new object[] { text });  
            }  
            else  
            {  
                this.textBox1.Text = text;  
            }  
        }  
  
        // This event handler starts the form's   
        // BackgroundWorker by calling RunWorkerAsync.  
        //  
        // The Text property of the TextBox control is set  
        // when the BackgroundWorker raises the RunWorkerCompleted  
        // event.  
        private void setTextBackgroundWorkerBtn_Click(  
            object sender,   
            EventArgs e)  
        {  
            this.backgroundWorker1.RunWorkerAsync();  
        }  
  
        // This event handler sets the Text property of the TextBox  
        // control. It is called on the thread that created the   
        // TextBox control, so the call is thread-safe.  
        //  
        // BackgroundWorker is the preferred way to perform asynchronous  
        // operations.  
  
        private void backgroundWorker1_RunWorkerCompleted(  
            object sender,   
            RunWorkerCompletedEventArgs e)  
        {  
            this.textBox1.Text =   
                "This text was set safely by BackgroundWorker.";  
        }  
  
        #region Windows Form Designer generated code  
  
        private void InitializeComponent()  
        {  
            this.textBox1 = new System.Windows.Forms.TextBox();  
            this.setTextUnsafeBtn = new System.Windows.Forms.Button();  
            this.setTextSafeBtn = new System.Windows.Forms.Button();  
            this.setTextBackgroundWorkerBtn = new System.Windows.Forms.Button();  
            this.backgroundWorker1 = new System.ComponentModel.BackgroundWorker();  
            this.SuspendLayout();  
            //   
            // textBox1  
            //   
            this.textBox1.Location = new System.Drawing.Point(12, 12);  
            this.textBox1.Name = "textBox1";  
            this.textBox1.Size = new System.Drawing.Size(240, 20);  
            this.textBox1.TabIndex = 0;  
            //   
            // setTextUnsafeBtn  
            //   
            this.setTextUnsafeBtn.Location = new System.Drawing.Point(15, 55);  
            this.setTextUnsafeBtn.Name = "setTextUnsafeBtn";  
            this.setTextUnsafeBtn.TabIndex = 1;  
            this.setTextUnsafeBtn.Text = "Unsafe Call";  
            this.setTextUnsafeBtn.Click += new System.EventHandler(this.setTextUnsafeBtn_Click);  
            //   
            // setTextSafeBtn  
            //   
            this.setTextSafeBtn.Location = new System.Drawing.Point(96, 55);  
            this.setTextSafeBtn.Name = "setTextSafeBtn";  
            this.setTextSafeBtn.TabIndex = 2;  
            this.setTextSafeBtn.Text = "Safe Call";  
            this.setTextSafeBtn.Click += new System.EventHandler(this.setTextSafeBtn_Click);  
            //   
            // setTextBackgroundWorkerBtn  
            //   
            this.setTextBackgroundWorkerBtn.Location = new System.Drawing.Point(177, 55);  
            this.setTextBackgroundWorkerBtn.Name = "setTextBackgroundWorkerBtn";  
            this.setTextBackgroundWorkerBtn.TabIndex = 3;  
            this.setTextBackgroundWorkerBtn.Text = "Safe BW Call";  
            this.setTextBackgroundWorkerBtn.Click += new System.EventHandler(this.setTextBackgroundWorkerBtn_Click);  
            //   
            // backgroundWorker1  
            //   
            this.backgroundWorker1.RunWorkerCompleted += new System.ComponentModel.RunWorkerCompletedEventHandler(this.backgroundWorker1_RunWorkerCompleted);  
            //   
            // Form1  
            //   
            this.ClientSize = new System.Drawing.Size(268, 96);  
            this.Controls.Add(this.setTextBackgroundWorkerBtn);  
            this.Controls.Add(this.setTextSafeBtn);  
            this.Controls.Add(this.setTextUnsafeBtn);  
            this.Controls.Add(this.textBox1);  
            this.Name = "Form1";  
            this.Text = "Form1";  
            this.ResumeLayout(false);  
            this.PerformLayout();  
  
        }  
  
        #endregion  
  
        [STAThread]  
        static void Main()  
        {  
            Application.EnableVisualStyles();  
            Application.Run(new Form1());  
        }  
  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.ComponentModel  
Imports System.Threading  
Imports System.Windows.Forms  
  
Public Class Form1  
   Inherits Form  
  
   ' This delegate enables asynchronous calls for setting  
   ' the text property on a TextBox control.  
   Delegate Sub StringArgReturningVoidDelegate([text] As String)  
  
   ' This thread is used to demonstrate both thread-safe and  
   ' unsafe ways to call a Windows Forms control.  
   Private demoThread As Thread = Nothing  
  
   ' This BackgroundWorker is used to demonstrate the   
   ' preferred way of performing asynchronous operations.  
   Private WithEvents backgroundWorker1 As BackgroundWorker  
  
   Private textBox1 As TextBox  
   Private WithEvents setTextUnsafeBtn As Button  
   Private WithEvents setTextSafeBtn As Button  
   Private WithEvents setTextBackgroundWorkerBtn As Button  
  
   Private components As System.ComponentModel.IContainer = Nothing  
  
   Public Sub New()  
      InitializeComponent()  
    End Sub  
  
   Protected Overrides Sub Dispose(disposing As Boolean)  
      If disposing AndAlso (components IsNot Nothing) Then  
         components.Dispose()  
      End If  
      MyBase.Dispose(disposing)  
    End Sub  
  
   ' This event handler creates a thread that calls a   
   ' Windows Forms control in an unsafe way.  
    Private Sub setTextUnsafeBtn_Click( _  
    ByVal sender As Object, _  
    ByVal e As EventArgs) Handles setTextUnsafeBtn.Click  
  
        Me.demoThread = New Thread( _  
        New ThreadStart(AddressOf Me.ThreadProcUnsafe))  
  
        Me.demoThread.Start()  
    End Sub  
  
   ' This method is executed on the worker thread and makes  
   ' an unsafe call on the TextBox control.  
   Private Sub ThreadProcUnsafe()  
      Me.textBox1.Text = "This text was set unsafely."  
   End Sub   
  
   ' This event handler creates a thread that calls a   
   ' Windows Forms control in a thread-safe way.  
    Private Sub setTextSafeBtn_Click( _  
    ByVal sender As Object, _  
    ByVal e As EventArgs) Handles setTextSafeBtn.Click  
  
        Me.demoThread = New Thread( _  
        New ThreadStart(AddressOf Me.ThreadProcSafe))  
  
        Me.demoThread.Start()  
    End Sub  
  
   ' This method is executed on the worker thread and makes  
   ' a thread-safe call on the TextBox control.  
   Private Sub ThreadProcSafe()  
      Me.SetText("This text was set safely.")  
    End Sub  
  
   ' This method demonstrates a pattern for making thread-safe  
   ' calls on a Windows Forms control.   
   '  
   ' If the calling thread is different from the thread that  
   ' created the TextBox control, this method creates a  
   ' StringArgReturningVoidDelegate and calls itself asynchronously using the  
   ' Invoke method.  
   '  
   ' If the calling thread is the same as the thread that created  
    ' the TextBox control, the Text property is set directly.   
  
    Private Sub SetText(ByVal [text] As String)  
  
        ' InvokeRequired required compares the thread ID of the  
        ' calling thread to the thread ID of the creating thread.  
        ' If these threads are different, it returns true.  
        If Me.textBox1.InvokeRequired Then  
            Dim d As New StringArgReturningVoidDelegate(AddressOf SetText)  
            Me.Invoke(d, New Object() {[text]})  
        Else  
            Me.textBox1.Text = [text]  
        End If  
    End Sub  
  
   ' This event handler starts the form's   
   ' BackgroundWorker by calling RunWorkerAsync.  
   '  
   ' The Text property of the TextBox control is set  
   ' when the BackgroundWorker raises the RunWorkerCompleted  
   ' event.  
    Private Sub setTextBackgroundWorkerBtn_Click( _  
    ByVal sender As Object, _  
    ByVal e As EventArgs) Handles setTextBackgroundWorkerBtn.Click  
        Me.backgroundWorker1.RunWorkerAsync()  
    End Sub  
  
   ' This event handler sets the Text property of the TextBox  
   ' control. It is called on the thread that created the   
   ' TextBox control, so the call is thread-safe.  
   '  
   ' BackgroundWorker is the preferred way to perform asynchronous  
   ' operations.  
    Private Sub backgroundWorker1_RunWorkerCompleted( _  
    ByVal sender As Object, _  
    ByVal e As RunWorkerCompletedEventArgs) _  
    Handles backgroundWorker1.RunWorkerCompleted  
        Me.textBox1.Text = _  
        "This text was set safely by BackgroundWorker."  
    End Sub  
  
   #Region "Windows Form Designer generated code"  
  
   Private Sub InitializeComponent()  
      Me.textBox1 = New System.Windows.Forms.TextBox()  
      Me.setTextUnsafeBtn = New System.Windows.Forms.Button()  
      Me.setTextSafeBtn = New System.Windows.Forms.Button()  
      Me.setTextBackgroundWorkerBtn = New System.Windows.Forms.Button()  
      Me.backgroundWorker1 = New System.ComponentModel.BackgroundWorker()  
      Me.SuspendLayout()  
      '   
      ' textBox1  
      '   
      Me.textBox1.Location = New System.Drawing.Point(12, 12)  
      Me.textBox1.Name = "textBox1"  
      Me.textBox1.Size = New System.Drawing.Size(240, 20)  
      Me.textBox1.TabIndex = 0  
      '   
      ' setTextUnsafeBtn  
      '   
      Me.setTextUnsafeBtn.Location = New System.Drawing.Point(15, 55)  
      Me.setTextUnsafeBtn.Name = "setTextUnsafeBtn"  
      Me.setTextUnsafeBtn.TabIndex = 1  
      Me.setTextUnsafeBtn.Text = "Unsafe Call"  
      '   
      ' setTextSafeBtn  
      '   
      Me.setTextSafeBtn.Location = New System.Drawing.Point(96, 55)  
      Me.setTextSafeBtn.Name = "setTextSafeBtn"  
      Me.setTextSafeBtn.TabIndex = 2  
      Me.setTextSafeBtn.Text = "Safe Call"  
      '   
      ' setTextBackgroundWorkerBtn  
      '   
      Me.setTextBackgroundWorkerBtn.Location = New System.Drawing.Point(177, 55)  
      Me.setTextBackgroundWorkerBtn.Name = "setTextBackgroundWorkerBtn"  
      Me.setTextBackgroundWorkerBtn.TabIndex = 3  
      Me.setTextBackgroundWorkerBtn.Text = "Safe BW Call"  
      '   
      ' backgroundWorker1  
      '   
      '   
      ' Form1  
      '   
      Me.ClientSize = New System.Drawing.Size(268, 96)  
      Me.Controls.Add(setTextBackgroundWorkerBtn)  
      Me.Controls.Add(setTextSafeBtn)  
      Me.Controls.Add(setTextUnsafeBtn)  
      Me.Controls.Add(textBox1)  
      Me.Name = "Form1"  
      Me.Text = "Form1"  
      Me.ResumeLayout(False)  
      Me.PerformLayout()  
   End Sub 'InitializeComponent   
  
   #End Region  
  
   <STAThread()>  _  
   Shared Sub Main()  
      Application.EnableVisualStyles()  
      Application.Run(New Form1())  
    End Sub  
End Class  
```  
  
```cpp  
#using <System.dll>  
#using <System.Windows.Forms.dll>  
#using <System.Drawing.dll>  
  
using namespace System;  
using namespace System::ComponentModel;  
using namespace System::Threading;  
using namespace System::Windows::Forms;  
  
namespace CrossThreadDemo  
{  
    public ref class Form1 : public Form  
    {  
        // This delegate enables asynchronous calls for setting  
        // the text property on a TextBox control.  
        delegate void StringArgReturningVoidDelegate(String^ text);  
  
        // This thread is used to demonstrate both thread-safe and  
        // unsafe ways to call a Windows Forms control.  
    private:  
        Thread^ demoThread;  
  
        // This BackgroundWorker is used to demonstrate the  
        // preferred way of performing asynchronous operations.  
    private:  
        BackgroundWorker^ backgroundWorker1;  
  
    private:  
        TextBox^ textBox1;  
    private:  
        Button^ setTextUnsafeBtn;  
    private:  
        Button^ setTextSafeBtn;  
    private:  
        Button^ setTextBackgroundWorkerBtn;  
  
    private:  
        System::ComponentModel::IContainer^ components;  
  
    public:  
        Form1()  
        {  
            components = nullptr;  
            InitializeComponent();  
        }  
  
    protected:  
        ~Form1()  
        {  
            if (components != nullptr)  
            {  
                delete components;  
            }  
        }  
  
        // This event handler creates a thread that calls a  
        // Windows Forms control in an unsafe way.  
    private:  
        void setTextUnsafeBtn_Click(Object^ sender, EventArgs^ e)  
        {  
            this->demoThread =  
                gcnew Thread(gcnew ThreadStart(this,&Form1::ThreadProcUnsafe));  
  
            this->demoThread->Start();  
        }  
  
        // This method is executed on the worker thread and makes  
        // an unsafe call on the TextBox control.  
    private:  
        void ThreadProcUnsafe()  
        {  
            this->textBox1->Text = "This text was set unsafely.";  
        }  
  
        // This event handler creates a thread that calls a  
        // Windows Forms control in a thread-safe way.  
    private:  
        void setTextSafeBtn_Click(Object^ sender, EventArgs^ e)  
        {  
            this->demoThread =  
                gcnew Thread(gcnew ThreadStart(this,&Form1::ThreadProcSafe));  
  
            this->demoThread->Start();  
        }  
  
        // This method is executed on the worker thread and makes  
        // a thread-safe call on the TextBox control.  
    private:  
        void ThreadProcSafe()  
        {  
            this->SetText("This text was set safely.");  
        }  
  
        // This method demonstrates a pattern for making thread-safe  
        // calls on a Windows Forms control.  
        //  
        // If the calling thread is different from the thread that  
        // created the TextBox control, this method creates a  
        // StringArgReturningVoidDelegate and calls itself asynchronously using the  
        // Invoke method.  
        //  
        // If the calling thread is the same as the thread that created  
        // the TextBox control, the Text property is set directly.  
  
    private:  
        void SetText(String^ text)  
        {  
            // InvokeRequired required compares the thread ID of the  
            // calling thread to the thread ID of the creating thread.  
            // If these threads are different, it returns true.  
            if (this->textBox1->InvokeRequired)  
            {  
                StringArgReturningVoidDelegate^ d =   
                    gcnew StringArgReturningVoidDelegate(this, &Form1::SetText);  
                this->Invoke(d, gcnew array<Object^> { text });  
            }  
            else  
            {  
                this->textBox1->Text = text;  
            }  
        }  
  
        // This event handler starts the form's  
        // BackgroundWorker by calling RunWorkerAsync.  
        //  
        // The Text property of the TextBox control is set  
        // when the BackgroundWorker raises the RunWorkerCompleted  
        // event.  
    private:  
        void setTextBackgroundWorkerBtn_Click(Object^ sender, EventArgs^ e)  
        {  
            this->backgroundWorker1->RunWorkerAsync();  
        }  
  
        // This event handler sets the Text property of the TextBox  
        // control. It is called on the thread that created the  
        // TextBox control, so the call is thread-safe.  
        //  
        // BackgroundWorker is the preferred way to perform asynchronous  
        // operations.  
  
    private:  
        void backgroundWorker1_RunWorkerCompleted(  
            Object^ sender,  
            RunWorkerCompletedEventArgs^ e)  
        {  
            this->textBox1->Text =  
                "This text was set safely by BackgroundWorker.";  
        }  
  
        #pragma region Windows Form Designer generated code  
  
    private:  
        void InitializeComponent()  
        {  
            this->textBox1 = gcnew System::Windows::Forms::TextBox();  
            this->setTextUnsafeBtn = gcnew System::Windows::Forms::Button();  
            this->setTextSafeBtn = gcnew System::Windows::Forms::Button();  
            this->setTextBackgroundWorkerBtn =   
                gcnew System::Windows::Forms::Button();  
            this->backgroundWorker1 =   
                gcnew System::ComponentModel::BackgroundWorker();  
            this->SuspendLayout();  
            //  
            // textBox1  
            //  
            this->textBox1->Location = System::Drawing::Point(12, 12);  
            this->textBox1->Name = "textBox1";  
            this->textBox1->Size = System::Drawing::Size(240, 20);  
            this->textBox1->TabIndex = 0;  
            //  
            // setTextUnsafeBtn  
            //  
            this->setTextUnsafeBtn->Location = System::Drawing::Point(15, 55);  
            this->setTextUnsafeBtn->Name = "setTextUnsafeBtn";  
            this->setTextUnsafeBtn->TabIndex = 1;  
            this->setTextUnsafeBtn->Text = "Unsafe Call";  
            this->setTextUnsafeBtn->Click +=   
                gcnew System::EventHandler(  
                this,&Form1::setTextUnsafeBtn_Click);  
            //  
            // setTextSafeBtn  
            //  
            this->setTextSafeBtn->Location = System::Drawing::Point(96, 55);  
            this->setTextSafeBtn->Name = "setTextSafeBtn";  
            this->setTextSafeBtn->TabIndex = 2;  
            this->setTextSafeBtn->Text = "Safe Call";  
            this->setTextSafeBtn->Click +=   
                gcnew System::EventHandler(this,&Form1::setTextSafeBtn_Click);  
            //  
            // setTextBackgroundWorkerBtn  
            //  
            this->setTextBackgroundWorkerBtn->Location =   
                System::Drawing::Point(177, 55);  
            this->setTextBackgroundWorkerBtn->Name =   
                "setTextBackgroundWorkerBtn";  
            this->setTextBackgroundWorkerBtn->TabIndex = 3;  
            this->setTextBackgroundWorkerBtn->Text = "Safe BW Call";  
            this->setTextBackgroundWorkerBtn->Click +=   
                gcnew System::EventHandler(  
                this,&Form1::setTextBackgroundWorkerBtn_Click);  
            //  
            // backgroundWorker1  
            //  
            this->backgroundWorker1->RunWorkerCompleted +=   
                gcnew System::ComponentModel::RunWorkerCompletedEventHandler(  
                this,&Form1::backgroundWorker1_RunWorkerCompleted);  
            //  
            // Form1  
            //  
            this->ClientSize = System::Drawing::Size(268, 96);  
            this->Controls->Add(this->setTextBackgroundWorkerBtn);  
            this->Controls->Add(this->setTextSafeBtn);  
            this->Controls->Add(this->setTextUnsafeBtn);  
            this->Controls->Add(this->textBox1);  
            this->Name = "Form1";  
            this->Text = "Form1";  
            this->ResumeLayout(false);  
            this->PerformLayout();  
  
        }  
  
        #pragma endregion  
    };  
}  
  
[STAThread]  
int main()  
{  
    Application::EnableVisualStyles();  
    Application::Run(gcnew CrossThreadDemo::Form1());  
}  
```  
  
 <span data-ttu-id="d18c2-150">アプリケーションを実行し、 **[Unsafe Call]** ボタンをクリックするとすぐに、テキスト ボックスに "Written by the main thread (メイン スレッドで作成されました)" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="d18c2-150">When you run the application and click the **Unsafe Call** button, you immediately see "Written by the main thread" in the text box.</span></span> <span data-ttu-id="d18c2-151">2 秒後、安全でない呼び出しが行われると、例外が発生したことが Visual Studio デバッガーにより示されます。</span><span class="sxs-lookup"><span data-stu-id="d18c2-151">Two seconds later, when the unsafe call is attempted, the Visual Studio debugger indicates that an exception occurred.</span></span> <span data-ttu-id="d18c2-152">デバッガーは、テキスト ボックスに直接書き込もうとしたバックグラウンド スレッドの該当行で停止します。</span><span class="sxs-lookup"><span data-stu-id="d18c2-152">The debugger stops at the line in the background thread that attempted to write directly to the text box.</span></span> <span data-ttu-id="d18c2-153">他の 2 つのボタンをテストするには、アプリケーションを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d18c2-153">You will have to restart the application to test the other two buttons.</span></span> <span data-ttu-id="d18c2-154">**[Safe Call]** ボタンをクリックすると、テキスト ボックスに "Written by the main thread (メイン スレッドで作成されました)" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="d18c2-154">When you click the **Safe Call** button, "Written by the main thread" appears in the text box.</span></span> <span data-ttu-id="d18c2-155">2 秒後、テキスト ボックスは "Written by the background thread (Invoke) (バックグラウンド スレッドで書き込まれました (呼び出し))" に設定されます。これは、 <xref:System.Windows.Forms.Control.Invoke%2A> メソッドが呼び出されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="d18c2-155">Two seconds later, the text box is set to "Written by the background thread (Invoke)", which indicates that the <xref:System.Windows.Forms.Control.Invoke%2A> method was called.</span></span> <span data-ttu-id="d18c2-156">**[Safe BW Call]** ボタンをクリックすると、テキスト ボックスに "Written by the main thread (メイン スレッドで作成されました)" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="d18c2-156">When you click the **Safe BW Call** button, "Written by the main thread" appears in the text box.</span></span> <span data-ttu-id="d18c2-157">2 秒後、テキスト ボックスは "Written by the main thread after the background thread completed (バックグラウンド スレッドの実行後にメイン スレッドで書き込まれました)" に設定されます。これは、 <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> の <xref:System.ComponentModel.BackgroundWorker> イベントのハンドラーが呼び出されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="d18c2-157">Two seconds later, the text box is set to "Written by the main thread after the background thread completed", which indicates that the handler for the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event of <xref:System.ComponentModel.BackgroundWorker> was called.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d18c2-158">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="d18c2-158">Robust Programming</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="d18c2-159">どのようなマルチスレッドを使用する場合でも、コードで深刻かつ複雑なバグが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d18c2-159">When you use multithreading of any sort, your code can be exposed to very serious and complex bugs.</span></span> <span data-ttu-id="d18c2-160">詳細については、マルチスレッドを使用するソリューションを実装する前に、「[マネージ スレッド処理の実施](../../../../docs/standard/threading/managed-threading-best-practices.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d18c2-160">For more information, see [Managed Threading Best Practices](../../../../docs/standard/threading/managed-threading-best-practices.md) before you implement any solution that uses multithreading.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d18c2-161">参照</span><span class="sxs-lookup"><span data-stu-id="d18c2-161">See Also</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 [<span data-ttu-id="d18c2-162">方法: バックグラウンドで操作を実行する</span><span class="sxs-lookup"><span data-stu-id="d18c2-162">How to: Run an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [<span data-ttu-id="d18c2-163">方法: バックグラウンド操作を使用するフォームを実装する</span><span class="sxs-lookup"><span data-stu-id="d18c2-163">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [<span data-ttu-id="d18c2-164">.NET Framework を使用したカスタム Windows フォーム コントロールの開発</span><span class="sxs-lookup"><span data-stu-id="d18c2-164">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="d18c2-165">Windows フォームとアンマネージ アプリケーション</span><span class="sxs-lookup"><span data-stu-id="d18c2-165">Windows Forms and Unmanaged Applications</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications.md)
