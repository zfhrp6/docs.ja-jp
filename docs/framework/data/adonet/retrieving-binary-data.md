---
title: "バイナリ データの取得"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 56c5a9e3-31f1-482f-bce0-ff1c41a658d0
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 43e937836911808789e2cad8affb395cc73ceb68
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="retrieving-binary-data"></a>バイナリ データの取得
既定では、 **DataReader**行全体のデータは使用するとすぐに行として受信したデータを読み込みます。 バイナリ ラージ オブジェクト (BLOB) には、1 行に収まらない数ギガバイトのデータが含まれる場合があるため、別の処理が必要です。 **Command.ExecuteReader**メソッド オーバー ロードを実行するには、<xref:System.Data.CommandBehavior>引数の既定の動作を変更する、 **DataReader**です。 渡すことができます<xref:System.Data.CommandBehavior.SequentialAccess>を**ExecuteReader**の既定の動作を変更する方法、 **DataReader**行のデータを読み込み中には、代わりにそれがデータを読み込む順番が受信できるようにします。 これは BLOB やその他の大きなデータ構造を読み込む場合に理想的な処理です。 この動作は、データ ソースによって異なる場合があります。 たとえば、Microsoft Access から BLOB を返すと、受け取ったデータから順に読み込むのではなく、BLOB 全体をメモリに読み込みます。  
  
 設定するときに、 **DataReader**を使用する**SequentialAccess**、返されるフィールドにアクセスするシーケンスを確認することが重要です。 既定の動作、 **DataReader**、次の行を読み取るまでは、任意の順序で返されるフィールドにアクセスすることができますが、使用可能になるとすぐに行全体が読み込まれます。 使用する場合**SequentialAccess**ただし、によって返されるフィールドにアクセスする必要があります、 **DataReader**の順序で。 たとえば、クエリが 3 つの列 (3 番目の列は BLOB) を返す場合、最初のフィールドおよび 2 番目のフィールドの値は、3 番目のフィールドの BLOB データにアクセスする前に返す必要があります。 最初のフィールドまたは 2 番目のフィールドの前に 3 番目のフィールドにアクセスした場合は、最初のフィールドと 2 番目のフィールドの値は使用できなくなります。 これは、ため**SequentialAccess**が変更、 **DataReader**シーケンスと、データにデータを返すことはできませんの後に、 **DataReader**を越えて読み取りができます。  
  
 BLOB フィールドのデータにアクセスするときに使用して、 **GetBytes**または**GetChars**型指定されたアクセサーの**DataReader**配列のデータを読み込みます。 使用することも**GetString**文字データです。 ただしです。 システム リソースを節約するためには、BLOB 値全体を 1 つの文字列変数に読み込むことは望ましくありません。 特定のバッファー サイズのデータを返すように指定する代わりに、返されたデータから読み込む先頭バイトまたは先頭文字の開始位置を指定できます。 **GetBytes**と**GetChars**が返されます、`long`をバイト数または返される文字数を表す値です。 Null 配列を渡す場合**GetBytes**または**GetChars**、返される long 型の値はバイトまたはキャラクター、BLOB 内の合計数になります。 オプションで、データ読み込みの開始位置を示す、配列内のインデックスを指定できます。  
  
## <a name="example"></a>例  
 次の例は、パブリッシャーから ID およびロゴを返します、 **pubs** Microsoft SQL Server のサンプル データベース。 発行者 ID (`pub_id`) は文字フィールドであり、ロゴはイメージ、つまり、BLOB です。 **ロゴ**フィールドはビットマップで、この例では、バイナリ データを使用して返されます**GetBytes**です。 フィールドには順番にアクセスする必要があるため、現在の行のデータに対して発行者 ID はロゴの前にアクセスされることに注意してください。  
  
```vb  
' Assumes that connection is a valid SqlConnection object.  
Dim command As SqlCommand = New SqlCommand( _  
  "SELECT pub_id, logo FROM pub_info", connection)  
  
' Writes the BLOB to a file (*.bmp).  
Dim stream As FileStream                   
' Streams the binary data to the FileStream object.  
Dim writer As BinaryWriter                 
' The size of the BLOB buffer.  
Dim bufferSize As Integer = 100        
' The BLOB byte() buffer to be filled by GetBytes.  
Dim outByte(bufferSize - 1) As Byte    
' The bytes returned from GetBytes.  
Dim retval As Long                     
' The starting position in the BLOB output.  
Dim startIndex As Long = 0             
  
' The publisher id to use in the file name.  
Dim pubID As String = ""              
  
' Open the connection and read data into the DataReader.  
connection.Open()  
Dim reader As SqlDataReader = command.ExecuteReader(CommandBehavior.SequentialAccess)  
  
Do While reader.Read()  
  ' Get the publisher id, which must occur before getting the logo.  
  pubID = reader.GetString(0)  
  
  ' Create a file to hold the output.  
  stream = New FileStream( _  
    "logo" & pubID & ".bmp", FileMode.OpenOrCreate, FileAccess.Write)  
  writer = New BinaryWriter(stream)  
  
  ' Reset the starting byte for a new BLOB.  
  startIndex = 0  
  
  ' Read bytes into outByte() and retain the number of bytes returned.  
  retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize)  
  
  ' Continue while there are bytes beyond the size of the buffer.  
  Do While retval = bufferSize  
    writer.Write(outByte)  
    writer.Flush()  
  
    ' Reposition start index to end of the last buffer and fill buffer.  
    startIndex += bufferSize  
    retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize)  
  Loop  
  
  ' Write the remaining buffer.  
  writer.Write(outByte, 0 , retval - 1)  
  writer.Flush()  
  
  ' Close the output file.  
  writer.Close()  
  stream.Close()  
Loop  
  
' Close the reader and the connection.  
reader.Close()  
connection.Close()  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object.  
SqlCommand command = new SqlCommand(  
  "SELECT pub_id, logo FROM pub_info", connection);  
  
// Writes the BLOB to a file (*.bmp).  
FileStream stream;                            
// Streams the BLOB to the FileStream object.  
BinaryWriter writer;                          
  
// Size of the BLOB buffer.  
int bufferSize = 100;                     
// The BLOB byte[] buffer to be filled by GetBytes.  
byte[] outByte = new byte[bufferSize];    
// The bytes returned from GetBytes.  
long retval;                              
// The starting position in the BLOB output.  
long startIndex = 0;                      
  
// The publisher id to use in the file name.  
string pubID = "";                       
  
// Open the connection and read data into the DataReader.  
connection.Open();  
SqlDataReader reader = command.ExecuteReader(CommandBehavior.SequentialAccess);  
  
while (reader.Read())  
{  
  // Get the publisher id, which must occur before getting the logo.  
  pubID = reader.GetString(0);    
  
  // Create a file to hold the output.  
  stream = new FileStream(  
    "logo" + pubID + ".bmp", FileMode.OpenOrCreate, FileAccess.Write);  
  writer = new BinaryWriter(stream);  
  
  // Reset the starting byte for the new BLOB.  
  startIndex = 0;  
  
  // Read bytes into outByte[] and retain the number of bytes returned.  
  retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize);  
  
  // Continue while there are bytes beyond the size of the buffer.  
  while (retval == bufferSize)  
  {  
    writer.Write(outByte);  
    writer.Flush();  
  
    // Reposition start index to end of last buffer and fill buffer.  
    startIndex += bufferSize;  
    retval = reader.GetBytes(1, startIndex, outByte, 0, bufferSize);  
  }  
  
  // Write the remaining buffer.  
  writer.Write(outByte, 0, (int)retval);  
  writer.Flush();  
  
  // Close the output file.  
  writer.Close();  
  stream.Close();  
}  
  
// Close the reader and the connection.  
reader.Close();  
connection.Close();  
```  
  
## <a name="see-also"></a>参照  
 [Datareader の操作](http://msdn.microsoft.com/en-us/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [SQL Server のバイナリ データと大きな値のデータ](../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター](http://go.microsoft.com/fwlink/?LinkId=217917)
