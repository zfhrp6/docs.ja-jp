---
title: "マルチスレッド プロシージャのパラメーターと戻り値 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: ba63c30c-d9f0-4962-b5c7-9d83ba851e6a
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fec0ad955439f0cd683ad56c8d6433eed2417304
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="parameters-and-return-values-for-multithreaded-procedures-c"></a>マルチスレッド プロシージャのパラメーターと戻り値 (C#)
マルチスレッド アプリケーションでの値の受け渡しは複雑です。それは、引数を受け取らず値を返さないプロシージャへの参照をスレッド クラスのコンストラクターに渡す必要があるためです。 以下のセクションでは、異なるスレッドのプロシージャからパラメーターを指定して値を返す単純な方法を示します。  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a>マルチスレッド プロシージャのパラメーターの指定  
 マルチスレッド メソッドの呼び出しにパラメーターを指定する最良の方法は、クラスにターゲット メソッドをラップし、新規スレッドのパラメーターとして機能するフィールドをそのクラスに対して定義することです。 この方法の利点は、新規スレッドを開始するたびに独自のパラメーターでクラスの新規インスタンスを作成できることです。 たとえば、次のコードに示すように三角形の面積を計算する関数があるとします。  
  
```csharp  
double CalcArea(double Base, double Height)  
{  
    return 0.5 * Base * Height;  
}  
```  
  
 次に示すように、`CalcArea` 関数をラップして入力パラメーターを格納するフィールドを作成するクラスを記述できます。  
  
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
  
 `AreaClass` を使用するには、次のコードに示すように `AreaClass` オブジェクトを作成し、`Base` プロパティと `Height` プロパティを設定します。  
  
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
  
 `TestArea` プロシージャは `CalcArea` メソッドの呼び出し後に `Area` フィールドの値を確認しないことに注意してください。 `CalcArea` は別のスレッドで実行されるため、`Thread.Start` を呼び出した直後に確認する場合は、`Area` フィールドが設定されているとは限りません。 次のセクションでは、マルチスレッド プロシージャから値を返す適切な方法について説明します。  
  
## <a name="returning-values-from-multithreaded-procedures"></a>マルチスレッド プロシージャから値を返す  
 異なるスレッドで実行されるプロシージャの場合、値を返す動作は複雑になります。プロシージャは関数にすることができず、`ByRef` 引数を使用できないからです。 値を返す最も簡単な方法は、<xref:System.ComponentModel.BackgroundWorker> コンポーネントを使ってスレッドを管理し、タスクが完了したときにイベントを生成し、結果をイベント ハンドラーで処理することです。  
  
 次の例では、別のスレッドで実行中のプロシージャからイベントを発生させて値を返します。  
  
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
  
 スレッド プールのスレッドにパラメーターと戻り値を提供するには、<xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> メソッドの省略可能な `ByVal` 状態オブジェクト変数を使用します。 スレッド タイマーのスレッドもこの目的で状態オブジェクトをサポートしています。 スレッド プールおよびスレッド タイマーの詳細については、「[スレッド プール (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)」および「[スレッド タイマー (C#)](../../../../csharp/programming-guide/concepts/threading/thread-timers.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: BackgroundWorker コンポーネントでのマルチスレッド (C#)](../../../../csharp/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)  
 [スレッド プール (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)  
 [スレッドの同期 (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)  
 [イベント](../../../../csharp/programming-guide/events/index.md)  
 [マルチスレッド アプリケーション (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)  
 [デリゲート](../../../../csharp/programming-guide/delegates/index.md)  
 [コンポーネントのマルチスレッド](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)
