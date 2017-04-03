---
title: "IDisposable を実装するオブジェクトの使用"
description: "IDisposable を実装するオブジェクトの使用"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/19/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: df780a6e-734e-44b8-9747-9f7783f79e20
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 63ad1233b5eab63670fd51f41f86269f643209a7
ms.lasthandoff: 03/02/2017

---

# <a name="using-objects-that-implement-idisposable"></a>IDisposable を実装するオブジェクトの使用

共通言語ランタイムのガベージ コレクターは、アンマネージ オブジェクトによって使用されているメモリを解放しますが、アンマネージ リソースを使用する型は、このアンマネージ メモリが解放されるように [IDisposable](xref:System.IDisposable) インターフェイスを実装します。 [IDisposable](xref:System.IDisposable) を実装するオブジェクトを使い終わったら、オブジェクトの [IDisposable.Dispose](xref:System.IDisposable.Dispose) の実装を呼び出す必要があります。 2 つの方法のいずれかでこれを行うことができます。

* C# の `using` ステートメントまたは Visual Basic の `Using` ステートメントを使用します。

* `try/finally` ブロックを実装します。 

## <a name="the-using-statement"></a>using ステートメント

C# の `using` ステートメントおよび Visual Basic の `Using` ステートメントを使用すると、オブジェクトの作成時やクリーンアップ時に記述する必要のあるコードが簡略化されます。 `using` ステートメントは、1 つ以上のリソースを取得し、指定されたステートメントを実行し、オブジェクトを自動的に破棄します。 ただし、`using` ステートメントは、オブジェクトが構築されるメソッドのスコープ内で使用されるオブジェクトに対してのみ有効です。 

次の例では、`using` ステートメントを使用して [System.IO.StreamReader](xref:System.IO.StreamReader) オブジェクトを作成し解放します。

```csharp
using System;
using System.IO;

public class Example
{
   public static void Main()
   {
      Char[] buffer = new Char[50];
      using (StreamReader s = new StreamReader("File1.txt")) {
         int charsRead = 0;
         while (s.Peek() != -1) {
            charsRead = s.Read(buffer, 0, buffer.Length);
            //
            // Process characters read.
            //   
         }
         s.Close();    
      }

   }
}
```

```vb
Imports System.IO

Module Example
   Public Sub Main()
      Dim buffer(49) As Char
      Using s As New StreamReader("File1.txt")
         Dim charsRead As Integer
         Do While s.Peek() <> -1
            charsRead = s.Read(buffer, 0, buffer.Length)         
            ' 
            ' Process characters read.
            '
         Loop
         s.Close()
      End Using
   End Sub
End Module
```

[StreamReader](xref:System.IO.StreamReader) クラスは [IDisposable](xref:System.IDisposable) インターフェイスを実装し、これはアンマネージ リソースを使用することを示していますが、例では [StreamReader.Dispose](xref:System.IO.StreamReader.Dispose(System.Boolean)) メソッドを明示的に呼び出していないことに注意してください。 C# または Visual Basic コンパイラが `using` ステートメントを見つけると、明示的に `try/finally` ブロックを含む次のコードと同等の中間言語 (IL) を生成します。 

```csharp
using System;
using System.IO;

public class Example
{
   public static void Main()
   {
      Char[] buffer = new Char[50];
      {
         StreamReader s = new StreamReader("File1.txt"); 
         try {
            int charsRead = 0;
            while (s.Peek() != -1) {
               charsRead = s.Read(buffer, 0, buffer.Length);
               //
               // Process characters read.
               //   
            }
            s.Close();
         }
         finally {
            if (s != null)
               ((IDisposable)s).Dispose();     
         }       
      }
   }
}
```

```vb
Imports System.IO

Module Example
   Public Sub Main()
      Dim buffer(49) As Char
''      Dim s As New StreamReader("File1.txt")
With s As New StreamReader("File1.txt")
      Try
         Dim charsRead As Integer
         Do While s.Peek() <> -1
            charsRead = s.Read(buffer, 0, buffer.Length)         
            ' 
            ' Process characters read.
            '
         Loop
         s.Close()
      Finally
         If s IsNot Nothing Then DirectCast(s, IDisposable).Dispose()
      End Try
End With
   End Sub
End Module
```

また、C# の `using` ステートメントでは、単一のステートメントで複数のリソースを取得できます。そのようなステートメントは、内部的には複数の using ステートメントを入れ子にした場合と同等です。 次の例では、2 つの異なるファイルの内容を読み取るために、[StreamReader](xref:System.IO.StreamReader) の&2; つのオブジェクトをインスタンス化します。 

```csharp
using System;
using System.IO;

public class Example
{
   public static void Main()
   {
      Char[] buffer1 = new Char[50], buffer2 = new Char[50];

      using (StreamReader version1 = new StreamReader("file1.txt"),
                          version2 = new StreamReader("file2.txt")) {
         int charsRead1, charsRead2 = 0;
         while (version1.Peek() != -1 && version2.Peek() != -1) {
            charsRead1 = version1.Read(buffer1, 0, buffer1.Length);
            charsRead2 = version2.Read(buffer2, 0, buffer2.Length);
            //
            // Process characters read.
            //
         }
         version1.Close();
         version2.Close();
      }
   }
}
```

## <a name="tryfinally-block"></a>Try/Finally ブロック

`using` ステートメントで `try/finally` ブロックをラップする代わりに、`try/finally` ブロックを直接実装することもできます。 これは、個人のコーディング スタイルであることも、次のいずれかの理由からそうすることもあります。 

* `catch` ブロックでスローされた例外をすべて処理する `try` ブロックを含めるため。 そうしないと、`try/catch` ブロックがない場合に `using` ブロック内でスローされた例外と同様に、`using` ステートメントによってスローされた例外は処理されません。 

* 宣言されたブロックに対してスコープがローカルでない [IDisposable](xref:System.IDisposable) を実装するオブジェクトをインスタンス化するため。 

次の例は前の例に似ていますが、`try/catch/finally` ブロックを使用して、[StreamReader](xref:System.IO.StreamReader) オブジェクトのインスタンス化、使用、破棄を実行し、[StreamReader](xref:System.IO.StreamReader) コンストラクターと [ReadToEnd](xref:System.IO.StreamReader.ReadToEnd) メソッドによってスローされた例外を処理しています。 [Dispose](xref:System.IDisposable.Dispose) メソッドを呼び出す前に [IDisposable](xref:System.IDisposable) を実装するオブジェクトが `null` でないことを `finally` ブロックのコードがチェックしていることに注意してください。 これを行わない場合、実行時に [NullReferenceException](xref:System.NullReferenceException) 例外が発生する可能性があります。 

```csharp
using System;
using System.Globalization;
using System.IO;

public class Example
{
   public static void Main()
   {
      StreamReader sr = null;
      try {
         sr = new StreamReader("file1.txt");
         String contents = sr.ReadToEnd();
         sr.Close();
         Console.WriteLine("The file has {0} text elements.", 
                           new StringInfo(contents).LengthInTextElements);    
      }      
      catch (FileNotFoundException) {
         Console.WriteLine("The file cannot be found.");
      }   
      catch (IOException) {
         Console.WriteLine("An I/O error has occurred.");
      }
      catch (OutOfMemoryException) {
         Console.WriteLine("There is insufficient memory to read the file.");   
      }
      finally {
         if (sr != null) sr.Dispose();     
      }
   }
}
```

```vb
Imports System.Globalization
Imports System.IO

Module Example
   Public Sub Main()
      Dim sr As StreamReader = Nothing
      Try 
         sr = New StreamReader("file1.txt")
         Dim contents As String = sr.ReadToEnd()
         sr.Close()
         Console.WriteLine("The file has {0} text elements.", 
                           New StringInfo(contents).LengthInTextElements)    
      Catch e As FileNotFoundException
         Console.WriteLine("The file cannot be found.")
      Catch e As IOException
         Console.WriteLine("An I/O error has occurred.")
      Catch e As OutOfMemoryException
         Console.WriteLine("There is insufficient memory to read the file.")   
      Finally 
         If sr IsNot Nothing Then sr.Dispose()     
      End Try
   End Sub
End Module
```

この基本パターンを利用できるのは、プログラミング言語で `using` ステートメントがサポートされていないが、[Dispose](xref:System.IDisposable.Dispose) メソッドを直接呼び出すことはできるため、`try/finally` ブロックの実装を選択した場合、または実装する必要がある場合です。 

## <a name="see-also"></a>関連項目

[アンマネージ リソースのクリーンアップ](unmanaged.md)



