---
title: "方法 : Windows フォーム ProgressBar コントロールによって表示される値を設定する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Increment メソッド"
  - "PerformStep メソッド"
  - "プログレス コントロール, 設定 (表示される値を)"
  - "ProgressBar コントロール [Windows フォーム], 設定 (表示される値を)"
  - "Step プロパティ"
  - "Value プロパティ"
ms.assetid: 0e5010ad-1e9a-4271-895e-5a3d24d37a26
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : Windows フォーム ProgressBar コントロールによって表示される値を設定する
> [!IMPORTANT]
>  <xref:System.Windows.Forms.ToolStripProgressBar> コントロールは、<xref:System.Windows.Forms.ProgressBar> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.ProgressBar> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] では、<xref:System.Windows.Forms.ProgressBar> コントロールに値を表示する方法として、いくつかの異なる方法があります。  どの方法を選択するかは、実行するタスクや解決しようとする問題によって決まります。  選択できる方法を次の表に示します。  
  
|方法|Description|  
|--------|-----------------|  
|<xref:System.Windows.Forms.ProgressBar> コントロールの値を直接設定する。|この方法は、データ ソースからレコードを読み取る場合など、測定する項目の合計数がわかっている場合に便利です。  また、値を 1 回か 2 回だけ設定すれば済む場合も、この方法が簡単です。  さらに、プログレス バーに表示される値を減らす必要がある場合にも、この方法を使用します。|  
|<xref:System.Windows.Forms.ProgressBar> の表示を固定された値だけ増加させる。|この方法は、既知の総数から処理された経過時間やファイル数など、最小値と最大値の間の単純なカウントを表示する場合に便利です。|  
|<xref:System.Windows.Forms.ProgressBar> の表示を可変の値だけ増加させる。|この方法は、表示される値を複数回、それぞれ異なる量だけ変化させる必要がある場合に便利です。  たとえば、ディスクにいくつかのファイルを書き込みながら、消費されたハード ディスク容量を表示する場合などです。|  
  
 プログレス バーに表示される値を設定する最も直接的な方法は、<xref:System.Windows.Forms.ProgressBar.Value%2A> プロパティを設定することです。  この操作は、デザイン時でも実行時でも実行できます。  
  
### ProgressBar の値を直接設定するには  
  
1.  <xref:System.Windows.Forms.ProgressBar> コントロールの <xref:System.Windows.Forms.ProgressBar.Minimum%2A> 値および <xref:System.Windows.Forms.ProgressBar.Maximum%2A> 値を設定します。  
  
2.  コードで、そのコントロールの <xref:System.Windows.Forms.ProgressBar.Value%2A> プロパティを、設定した最小値と最大値の間の整数値に設定します。  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.ProgressBar.Value%2A> プロパティを、<xref:System.Windows.Forms.ProgressBar.Minimum%2A> プロパティおよび <xref:System.Windows.Forms.ProgressBar.Maximum%2A> プロパティによって設定された範囲外に設定すると、コントロールが <xref:System.ArgumentException> 例外をスローします。  
  
     <xref:System.Windows.Forms.ProgressBar> の値を直接設定する方法を次のコード例に示します。  このコードは、データ ソースからレコードを読み取り、1 レコード読み取るごとにプログレス バーとラベルを更新します。  この例では、フォームに <xref:System.Windows.Forms.Label> コントロール、<xref:System.Windows.Forms.ProgressBar> コントロール、およびデータ テーブルがあり、データ テーブルの `CustomerRow`  という行に `FirstName`  および `Last Name`  というフィールドがあることが必須条件です。  
  
    ```vb  
    Public Sub CreateNewRecords()  
       ' Sets the progress bar's Maximum property to  
       ' the total number of records to be created.  
       ProgressBar1.Maximum = 20  
  
       ' Creates a new record in the dataset.  
       ' NOTE: The code below will not compile, it merely  
       ' illustrates how the progress bar would be used.  
       Dim anyRow As CustomerRow = DatasetName.ExistingTable.NewRow  
       anyRow.FirstName = "Stephen"  
       anyRow.LastName = "James"  
       ExistingTable.Rows.Add(anyRow)  
  
       ' Increases the value displayed by the progress bar.  
       ProgressBar1.Value += 1  
       ' Updates the label to show that a record was read.  
       Label1.Text = "Records Read = " & ProgressBar1.Value.ToString()  
    End Sub  
  
    ```  
  
    ```csharp  
    public void createNewRecords()  
    {  
       // Sets the progress bar's Maximum property to  
       // the total number of records to be created.  
       progressBar1.Maximum = 20;  
  
       // Creates a new record in the dataset.  
       // NOTE: The code below will not compile, it merely  
       // illustrates how the progress bar would be used.  
       CustomerRow anyRow = DatasetName.ExistingTable.NewRow();  
       anyRow.FirstName = "Stephen";  
       anyRow.LastName = "James";  
       ExistingTable.Rows.Add(anyRow);  
  
       // Increases the value displayed by the progress bar.  
       progressBar1.Value += 1;  
       // Updates the label to show that a record was read.  
       label1.Text = "Records Read = " + progressBar1.Value.ToString();  
    }  
    ```  
  
     固定された間隔で増加する進行状況を表示する場合は、値を設定してから、その間隔で <xref:System.Windows.Forms.ProgressBar> コントロールの値を増加させるメソッドを呼び出します。  これは、タイマーなどのように、進行状況を全体に対する割合として表さない状況で便利です。  
  
### プログレス バーを固定された値だけ増加させるには  
  
1.  <xref:System.Windows.Forms.ProgressBar> コントロールの <xref:System.Windows.Forms.ProgressBar.Minimum%2A> 値および <xref:System.Windows.Forms.ProgressBar.Maximum%2A> 値を設定します。  
  
2.  コントロールの <xref:System.Windows.Forms.ProgressBar.Step%2A> プロパティに、プログレス バーの表示値を増加させる量を表す整数を設定します。  
  
3.  <xref:System.Windows.Forms.ProgressBar.PerformStep%2A> メソッドを呼び出して、表示される値を <xref:System.Windows.Forms.ProgressBar.Step%2A> プロパティに設定した量だけ変更します。  
  
     コピー操作中にプログレス バーにファイル数を表示させる方法を次のコード例に示します。  
  
     この例では、各ファイルがメモリに読み込まれるたびに、プログレス バーおよびラベルが、読み込んだファイルの合計数を反映するように更新されます。  この例では、フォームに <xref:System.Windows.Forms.Label> コントロールおよび <xref:System.Windows.Forms.ProgressBar> コントロールがあることが必須条件です。  
  
    ```vb  
    Public Sub LoadFiles()  
       ' Sets the progress bar's minimum value to a number representing  
       ' no operations complete -- in this case, no files read.  
       ProgressBar1.Minimum = 0  
       ' Sets the progress bar's maximum value to a number representing  
       ' all operations complete -- in this case, all five files read.  
       ProgressBar1.Maximum = 5  
       ' Sets the Step property to amount to increase with each iteration.  
       ' In this case, it will increase by one with every file read.  
       ProgressBar1.Step = 1  
  
       ' Dimensions a counter variable.  
       Dim i As Integer  
       ' Uses a For...Next loop to iterate through the operations to be  
       ' completed. In this case, five files are to be copied into memory,  
       ' so the loop will execute 5 times.  
       For i = 0 To 4  
          ' Insert code to copy a file  
          ProgressBar1.PerformStep()  
          ' Update the label to show that a file was read.  
          Label1.Text = "# of Files Read = " & ProgressBar1.Value.ToString  
       Next i  
    End Sub  
  
    ```  
  
    ```csharp  
    public void loadFiles()  
    {  
       // Sets the progress bar's minimum value to a number representing  
       // no operations complete -- in this case, no files read.  
       progressBar1.Minimum = 0;  
       // Sets the progress bar's maximum value to a number representing  
       // all operations complete -- in this case, all five files read.  
       progressBar1.Maximum = 5;  
       // Sets the Step property to amount to increase with each iteration.  
       // In this case, it will increase by one with every file read.  
       progressBar1.Step = 1;  
  
       // Uses a for loop to iterate through the operations to be  
       // completed. In this case, five files are to be copied into memory,  
       // so the loop will execute 5 times.  
       for (int i = 0; i <= 4; i++)  
       {  
          // Inserts code to copy a file  
          progressBar1.PerformStep();  
          // Updates the label to show that a file was read.  
          label1.Text = "# of Files Read = " + progressBar1.Value.ToString();  
       }  
    }  
    ```  
  
     最後に、プログレス バーに表示される値をそのたびに異なる量だけ増加させる方法を説明します。  これは、異なるサイズのファイルをハード ディスクに書き込む場合や、進行状況を全体に対する割合で表す場合など、一連の操作を追跡する場合に便利です。  
  
### プログレス バーを動的な値だけ増加させるには  
  
1.  <xref:System.Windows.Forms.ProgressBar> コントロールの <xref:System.Windows.Forms.ProgressBar.Minimum%2A> 値および <xref:System.Windows.Forms.ProgressBar.Maximum%2A> 値を設定します。  
  
2.  <xref:System.Windows.Forms.ProgressBar.Increment%2A> メソッドを呼び出して、表示される値を指定した整数だけ変化させます。  
  
     コピー操作中に消費されたディスク容量をプログレス バーで計算する方法を次のコード例に示します。  
  
     この例では、各ファイルがハード ディスクに書き込まれるたびに、プログレス バーとラベルが更新され、使用できるハード ディスク容量が反映されます。  この例では、フォームに <xref:System.Windows.Forms.Label> コントロールおよび <xref:System.Windows.Forms.ProgressBar> コントロールがあることが必須条件です。  
  
    ```vb  
    Public Sub ReadFiles()  
       ' Sets the progress bar's minimum value to a number   
       ' representing the hard disk space before the files are read in.  
       ' You will most likely have to set this using a system call.  
       ' NOTE: The code below is meant to be an example and  
       ' will not compile.  
       ProgressBar1.Minimum = AvailableDiskSpace()  
       ' Sets the progress bar's maximum value to a number   
       ' representing the total hard disk space.  
       ' You will most likely have to set this using a system call.  
       ' NOTE: The code below is meant to be an example   
       ' and will not compile.  
       ProgressBar1.Maximum = TotalDiskSpace()  
  
       ' Dimension a counter variable.  
       Dim i As Integer  
       ' Uses a For...Next loop to iterate through the operations to be  
       ' completed. In this case, five files are to be written to the disk,  
       ' so it will execute the loop 5 times.  
       For i = 1 To 5  
          ' Insert code to read a file into memory and update file size.  
          ' Increases the progress bar's value based on the size of   
          ' the file currently being written.  
          ProgressBar1.Increment(FileSize)  
          ' Updates the label to show available drive space.  
          Label1.Text = "Current Disk Space Used = " &_   
          ProgressBar1.Value.ToString()  
       Next i  
    End Sub  
  
    ```  
  
    ```csharp  
    public void readFiles()  
    {  
       // Sets the progress bar's minimum value to a number   
       // representing the hard disk space before the files are read in.  
       // You will most likely have to set this using a system call.  
       // NOTE: The code below is meant to be an example and   
       // will not compile.  
       progressBar1.Minimum = AvailableDiskSpace();  
       // Sets the progress bar's maximum value to a number   
       // representing the total hard disk space.  
       // You will most likely have to set this using a system call.  
       // NOTE: The code below is meant to be an example   
       // and will not compile.  
       progressBar1.Maximum = TotalDiskSpace();  
  
       // Uses a for loop to iterate through the operations to be  
       // completed. In this case, five files are to be written  
       // to the disk, so it will execute the loop 5 times.  
       for (int i = 1; i<= 5; i++)  
       {  
          // Insert code to read a file into memory and update file size.  
          // Increases the progress bar's value based on the size of   
          // the file currently being written.  
          progressBar1.Increment(FileSize);  
          // Updates the label to show available drive space.  
          label1.Text = "Current Disk Space Used = " + progressBar1.Value.ToString();  
       }  
    }  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.ProgressBar>   
 <xref:System.Windows.Forms.ToolStripProgressBar>   
 [ProgressBar コントロールの概要](../../../../docs/framework/winforms/controls/progressbar-control-overview-windows-forms.md)   
 [ProgressBar コントロール](../../../../docs/framework/winforms/controls/progressbar-control-windows-forms.md)