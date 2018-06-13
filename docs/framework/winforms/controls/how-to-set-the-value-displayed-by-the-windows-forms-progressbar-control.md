---
title: '方法 : Windows フォーム ProgressBar コントロールによって表示される値を設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ProgressBar control [Windows Forms], setting value displayed
- progress controls [Windows Forms], setting value displayed
ms.assetid: 0e5010ad-1e9a-4271-895e-5a3d24d37a26
ms.openlocfilehash: 66093cacea4f76ab65af40658f03c03ce7560f0d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540119"
---
# <a name="how-to-set-the-value-displayed-by-the-windows-forms-progressbar-control"></a>方法 : Windows フォーム ProgressBar コントロールによって表示される値を設定する
> [!IMPORTANT]
>  <xref:System.Windows.Forms.ToolStripProgressBar> コントロールは、<xref:System.Windows.Forms.ProgressBar> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.ProgressBar> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]内で指定された値を表示するいくつかの方法を提供する、<xref:System.Windows.Forms.ProgressBar>コントロール。 選択するための方法は、前のタスクまたは当面の問題によって異なります。 次の表は、ことができます、方法を示します。  
  
|方法|説明|  
|--------------|-----------------|  
|値を設定、<xref:System.Windows.Forms.ProgressBar>直接制御します。|この方法は、データ ソースからのレコードの読み取りなど、関連を測定する項目の合計がわかっている場合のタスクに役立ちます。 さらに、値を 1 ~ 2 回設定するだけで済みますこれがそれを実行する簡単な方法です。 最後に、進行状況バーに表示される値を小さく必要がある場合は、このプロセスを使用します。|  
|増加、<xref:System.Windows.Forms.ProgressBar>固定値を表示します。|この方法は、最小値と最大値の場合は、経過時間や、既知の合計から処理されたファイルの数など、間の単純なカウントを表示する場合に便利です。|  
|増加、<xref:System.Windows.Forms.ProgressBar>が変化する値を表示します。|この方法は、表示されている値をそれぞれ異なる量の回数を変更する必要がある場合に便利です。 例は、一連のファイルをディスクに書き込み中に使用されているハード_ディスク領域の量を表示する場合します。|  
  
 進行状況バーに表示される値を設定する最も直接的な方法は、設定して、<xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティです。 これは、デザイン時に、または実行時に実行できます。  
  
### <a name="to-set-the-progressbar-value-directly"></a>プログレス バーの値を直接設定するには  
  
1.  設定、<xref:System.Windows.Forms.ProgressBar>コントロールの<xref:System.Windows.Forms.ProgressBar.Minimum%2A>と<xref:System.Windows.Forms.ProgressBar.Maximum%2A>値。  
  
2.  コードでは、設定コントロールの<xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティが確立されている最小値と最大値までの整数値にします。  
  
    > [!NOTE]
    >  設定した場合、<xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティによって確立された境界の外、<xref:System.Windows.Forms.ProgressBar.Minimum%2A>と<xref:System.Windows.Forms.ProgressBar.Maximum%2A>プロパティ、コントロールをスロー、<xref:System.ArgumentException>例外。  
  
     次のコード例を設定する方法を示しています、<xref:System.Windows.Forms.ProgressBar>直接値します。 コードでは、データ ソースからレコードを読み取り、データ レコードが読み取られるたびに、進行状況バーとラベルを更新します。 この例では、フォームがある必要があります、<xref:System.Windows.Forms.Label>コントロール、<xref:System.Windows.Forms.ProgressBar>と呼ばれる行のデータ テーブルとコントロール、`CustomerRow`で`FirstName`と`LastName`フィールドです。  
  
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
  
     固定された間隔でする進行状況を表示する場合は、値を設定および増加するメソッドを呼び出す、<xref:System.Windows.Forms.ProgressBar>その間隔でのコントロールの値。 これは、タイマーおよびその他のシナリオを表さない進行状況全体に占める割合として便利です。  
  
### <a name="to-increase-the-progress-bar-by-a-fixed-value"></a>固定値によって、進行状況バーを強化するには  
  
1.  設定、<xref:System.Windows.Forms.ProgressBar>コントロールの<xref:System.Windows.Forms.ProgressBar.Minimum%2A>と<xref:System.Windows.Forms.ProgressBar.Maximum%2A>値。  
  
2.  コントロールの設定<xref:System.Windows.Forms.ProgressBar.Step%2A>プログレス バーに時間を表す整数のプロパティに値が表示されます。  
  
3.  呼び出す、<xref:System.Windows.Forms.ProgressBar.PerformStep%2A>に設定した値によって示される値を変更するメソッドを<xref:System.Windows.Forms.ProgressBar.Step%2A>プロパティです。  
  
     次のコード例は、進行状況バーが、コピー操作でファイルの数を維持する方法を示しています。  
  
     次の例では、各ファイルがメモリに読み込まれると、進行状況バーとラベル更新されますファイルの合計数を読み取るを反映するようにします。 この例では、フォームがある必要があります、<xref:System.Windows.Forms.Label>コントロールと<xref:System.Windows.Forms.ProgressBar>コントロール。  
  
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
  
     最後に、プログレス バーに表示されるので、それぞれの増加は、一意の時間値を大きくことができます。 これは、機能は、一連のハード ディスクへのサイズの異なるファイルの書き込みや、全体に占める割合としての進行状況の測定など、一意の操作の追跡をすることは、ときに便利です。  
  
### <a name="to-increase-the-progress-bar-by-a-dynamic-value"></a>動的な値で進行状況バーを向上させる  
  
1.  設定、<xref:System.Windows.Forms.ProgressBar>コントロールの<xref:System.Windows.Forms.ProgressBar.Minimum%2A>と<xref:System.Windows.Forms.ProgressBar.Maximum%2A>値。  
  
2.  呼び出す、<xref:System.Windows.Forms.ProgressBar.Increment%2A>メソッドを指定する整数値に表示される値を変更します。  
  
     次のコード例は、どのように進行状況バーがコピー操作中にディスク領域が使用されてを計算することができますを示しています。  
  
     次の例では、各ファイルがハード ディスクに書き込まれると、進行状況バーとラベル更新されます使用可能なハード_ディスク領域の量を反映するようにします。 この例では、フォームがある必要があります、<xref:System.Windows.Forms.Label>コントロールと<xref:System.Windows.Forms.ProgressBar>コントロール。  
  
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
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.ProgressBar>  
 <xref:System.Windows.Forms.ToolStripProgressBar>  
 [ProgressBar コントロールの概要](../../../../docs/framework/winforms/controls/progressbar-control-overview-windows-forms.md)  
 [ProgressBar コントロール](../../../../docs/framework/winforms/controls/progressbar-control-windows-forms.md)
