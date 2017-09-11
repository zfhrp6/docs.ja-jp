---
title: "マルチスレッド プロシージャのパラメーターと戻り値 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: ba63c30c-d9f0-4962-b5c7-9d83ba851e6a
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5e377a006409dbae49b3c00297f69e8d55a01295
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="parameters-and-return-values-for-multithreaded-procedures-c"></a><span data-ttu-id="befa0-102">マルチスレッド プロシージャのパラメーターと戻り値 (C#)</span><span class="sxs-lookup"><span data-stu-id="befa0-102">Parameters and Return Values for Multithreaded Procedures (C#)</span></span>
<span data-ttu-id="befa0-103">マルチスレッド アプリケーションでの値の受け渡しは複雑です。それは、引数を受け取らず値を返さないプロシージャへの参照をスレッド クラスのコンストラクターに渡す必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="befa0-103">Supplying and returning values in a multithreaded application is complicated because the constructor for the thread class must be passed a reference to a procedure that takes no arguments and returns no value.</span></span> <span data-ttu-id="befa0-104">以下のセクションでは、異なるスレッドのプロシージャからパラメーターを指定して値を返す単純な方法を示します。</span><span class="sxs-lookup"><span data-stu-id="befa0-104">The following sections show some simple ways to supply parameters and return values from procedures on separate threads.</span></span>  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a><span data-ttu-id="befa0-105">マルチスレッド プロシージャのパラメーターの指定</span><span class="sxs-lookup"><span data-stu-id="befa0-105">Supplying Parameters for Multithreaded Procedures</span></span>  
 <span data-ttu-id="befa0-106">マルチスレッド メソッドの呼び出しにパラメーターを指定する最良の方法は、クラスにターゲット メソッドをラップし、新規スレッドのパラメーターとして機能するフィールドをそのクラスに対して定義することです。</span><span class="sxs-lookup"><span data-stu-id="befa0-106">The best way to supply parameters for a multithreaded method call is to wrap the target method in a class and define fields for that class that will serve as parameters for the new thread.</span></span> <span data-ttu-id="befa0-107">この方法の利点は、新規スレッドを開始するたびに独自のパラメーターでクラスの新規インスタンスを作成できることです。</span><span class="sxs-lookup"><span data-stu-id="befa0-107">The advantage of this approach is that you can create a new instance of the class, with its own parameters, every time you want to start a new thread.</span></span> <span data-ttu-id="befa0-108">たとえば、次のコードに示すように三角形の面積を計算する関数があるとします。</span><span class="sxs-lookup"><span data-stu-id="befa0-108">For example, suppose you have a function that calculates the area of a triangle, as in the following code:</span></span>  
  
```csharp  
double CalcArea(double Base, double Height)  
{  
    return 0.5 * Base * Height;  
}  
```  
  
 <span data-ttu-id="befa0-109">次に示すように、`CalcArea` 関数をラップして入力パラメーターを格納するフィールドを作成するクラスを記述できます。</span><span class="sxs-lookup"><span data-stu-id="befa0-109">You can write a class that wraps the `CalcArea` function and creates fields to store input parameters, as follows:</span></span>  
  
```csharp  
class AreaClass  
{  
    public double Base;  
    public double Height;  
    public double Area;  
    public void CalcArea()  
    {  
        Area = 0.5 * Base * Height;  
        MessageBox.Show("The area is: " + Area.ToString());  
    }  
}  
```  
  
 <span data-ttu-id="befa0-110">`AreaClass` を使用するには、次のコードに示すように `AreaClass` オブジェクトを作成し、`Base` プロパティと `Height` プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="befa0-110">To use the `AreaClass`, you can create an `AreaClass` object, and set the `Base` and `Height` properties as shown in the following code:</span></span>  
  
```csharp  
protected void TestArea()  
{  
    AreaClass AreaObject = new AreaClass();  
  
    System.Threading.Thread Thread =  
        new System.Threading.Thread(AreaObject.CalcArea);  
    AreaObject.Base = 30;  
    AreaObject.Height = 40;  
    Thread.Start();  
}  
```  
  
 <span data-ttu-id="befa0-111">`TestArea` プロシージャは `CalcArea` メソッドの呼び出し後に `Area` フィールドの値を確認しないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="befa0-111">Notice that the `TestArea` procedure does not check the value of the `Area` field after calling the `CalcArea` method.</span></span> <span data-ttu-id="befa0-112">`CalcArea` は別のスレッドで実行されるため、`Thread.Start` を呼び出した直後に確認する場合は、`Area` フィールドが設定されているとは限りません。</span><span class="sxs-lookup"><span data-stu-id="befa0-112">Because `CalcArea` runs on a separate thread, the `Area` field is not guaranteed to be set if you check it immediately after calling `Thread.Start`.</span></span> <span data-ttu-id="befa0-113">次のセクションでは、マルチスレッド プロシージャから値を返す適切な方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="befa0-113">The next section discusses a better way to return values from multithreaded procedures.</span></span>  
  
## <a name="returning-values-from-multithreaded-procedures"></a><span data-ttu-id="befa0-114">マルチスレッド プロシージャから値を返す</span><span class="sxs-lookup"><span data-stu-id="befa0-114">Returning Values from Multithreaded Procedures</span></span>  
 <span data-ttu-id="befa0-115">異なるスレッドで実行されるプロシージャの場合、値を返す動作は複雑になります。プロシージャは関数にすることができず、`ByRef` 引数を使用できないからです。</span><span class="sxs-lookup"><span data-stu-id="befa0-115">Returning values from procedures that run on separate threads is complicated by the fact that the procedures cannot be functions and cannot use `ByRef` arguments.</span></span> <span data-ttu-id="befa0-116">値を返す最も簡単な方法は、<xref:System.ComponentModel.BackgroundWorker> コンポーネントを使ってスレッドを管理し、タスクが完了したときにイベントを生成し、結果をイベント ハンドラーで処理することです。</span><span class="sxs-lookup"><span data-stu-id="befa0-116">The easiest way to return values is to use the <xref:System.ComponentModel.BackgroundWorker> component to manage your threads and raise an event when the task is done, and process the results with an event handler.</span></span>  
  
 <span data-ttu-id="befa0-117">次の例では、別のスレッドで実行中のプロシージャからイベントを発生させて値を返します。</span><span class="sxs-lookup"><span data-stu-id="befa0-117">The following example returns a value by raising an event from a procedure running on a separate thread:</span></span>  
  
```csharp  
class AreaClass2  
{  
    public double Base;  
    public double Height;  
    public double CalcArea()  
    {  
        // Calculate the area of a triangle.  
        return 0.5 * Base * Height;  
    }  
}  
  
private System.ComponentModel.BackgroundWorker BackgroundWorker1  
    = new System.ComponentModel.BackgroundWorker();  
  
private void TestArea2()  
{  
    InitializeBackgroundWorker();  
  
    AreaClass2 AreaObject2 = new AreaClass2();  
    AreaObject2.Base = 30;  
    AreaObject2.Height = 40;  
  
    // Start the asynchronous operation.  
    BackgroundWorker1.RunWorkerAsync(AreaObject2);  
}  
  
private void InitializeBackgroundWorker()  
{  
    // Attach event handlers to the BackgroundWorker object.  
    BackgroundWorker1.DoWork +=  
        new System.ComponentModel.DoWorkEventHandler(BackgroundWorker1_DoWork);  
    BackgroundWorker1.RunWorkerCompleted +=  
        new System.ComponentModel.RunWorkerCompletedEventHandler(BackgroundWorker1_RunWorkerCompleted);  
}  
  
private void BackgroundWorker1_DoWork(  
    object sender,  
    System.ComponentModel.DoWorkEventArgs e)  
{  
    AreaClass2 AreaObject2 = (AreaClass2)e.Argument;  
    // Return the value through the Result property.  
    e.Result = AreaObject2.CalcArea();  
}  
  
private void BackgroundWorker1_RunWorkerCompleted(  
    object sender,  
    System.ComponentModel.RunWorkerCompletedEventArgs e)  
{  
    // Access the result through the Result property.  
    double Area = (double)e.Result;  
    MessageBox.Show("The area is: " + Area.ToString());  
}  
```  
  
 <span data-ttu-id="befa0-118">スレッド プールのスレッドにパラメーターと戻り値を提供するには、<xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> メソッドの省略可能な `ByVal` 状態オブジェクト変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="befa0-118">You can provide parameters and return values to thread-pool threads by using the optional `ByVal` state-object variable of the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method.</span></span> <span data-ttu-id="befa0-119">スレッド タイマーのスレッドもこの目的で状態オブジェクトをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="befa0-119">Thread-timer threads also support a state object for this purpose.</span></span> <span data-ttu-id="befa0-120">スレッド プールおよびスレッド タイマーの詳細については、「[スレッド プール (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)」および「[スレッド タイマー (C#)](../../../../csharp/programming-guide/concepts/threading/thread-timers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="befa0-120">For information on thread pooling and thread timers, see [Thread Pooling (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md) and [Thread Timers (C#)](../../../../csharp/programming-guide/concepts/threading/thread-timers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="befa0-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="befa0-121">See Also</span></span>  
 <span data-ttu-id="befa0-122">[チュートリアル: BackgroundWorker コンポーネントでのマルチスレッド (C#)](../../../../csharp/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md) </span><span class="sxs-lookup"><span data-stu-id="befa0-122">[Walkthrough: Multithreading with the BackgroundWorker Component (C#)](../../../../csharp/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md) </span></span>  
 <span data-ttu-id="befa0-123">[スレッド プール (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md) </span><span class="sxs-lookup"><span data-stu-id="befa0-123">[Thread Pooling (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md) </span></span>  
 <span data-ttu-id="befa0-124">[スレッドの同期 (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md) </span><span class="sxs-lookup"><span data-stu-id="befa0-124">[Thread Synchronization (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md) </span></span>  
 <span data-ttu-id="befa0-125">[イベント](../../../../csharp/programming-guide/events/index.md) </span><span class="sxs-lookup"><span data-stu-id="befa0-125">[Events](../../../../csharp/programming-guide/events/index.md) </span></span>  
 <span data-ttu-id="befa0-126">[マルチスレッド アプリケーション (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md) </span><span class="sxs-lookup"><span data-stu-id="befa0-126">[Multithreaded Applications (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md) </span></span>  
 <span data-ttu-id="befa0-127">[デリゲート](../../../../csharp/programming-guide/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="befa0-127">[Delegates](../../../../csharp/programming-guide/delegates/index.md) </span></span>  
 [<span data-ttu-id="befa0-128">コンポーネントのマルチスレッド</span><span class="sxs-lookup"><span data-stu-id="befa0-128">Multithreading in Components</span></span>](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)

