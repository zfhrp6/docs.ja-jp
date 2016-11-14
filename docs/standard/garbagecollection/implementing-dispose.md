---
title: "Dispose メソッドの実装"
description: "Dispose メソッドの実装"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: eca6cdc3-6a14-4296-86fb-1eb2f21455b0
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: dfe2cebfbcf1f4c2697683ebda8c1e11567fd015

---

# <a name="implementing-a-dispose-method"></a>Dispose メソッドの実装

アプリケーションによって使用されるアンマネージ リソースを解放するための [Dispose](xref:System.IDisposable.Dispose) メソッドを実装します。 .NET のガベージ コレクターは、アンマネージ メモリの割り当てや解放を行いません。 

Dispose パターンと呼ばれる、オブジェクトを破棄するパターンによって、オブジェクトの有効期間に順番が付けられます。 Dispose パターンは、ファイルおよびパイプ ハンドル、レジストリ ハンドル、待機ハンドル、アンマネージ メモリ ブロックのポインターなど、アンマネージ リソースにアクセスするオブジェクトでのみ使用されます。 これは、使用されていないマネージ オブジェクトの解放にはガベージ コレクターが非常に有効ですが、アンマネージ オブジェクトは解放できないためです。

Dispose パターンには 2 種類あります。

* 型で使用する各アンマネージ リソースをセーフ ハンドル (つまり、[System.Runtime.InteropServices.SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) から派生したクラス) でラップします。 この場合、[IDisposable](xref:System.IDisposable) インターフェイスと追加の `Dispose(Boolean)` メソッドを実装します。 これは推奨される方法で、[Object.Finalize](xref:System.Object.Finalize) メソッドをオーバーライドする必要がありません。 

> [!NOTE]
> [Microsoft.Win32.SafeHandles](xref:Microsoft.Win32.SafeHandles) 名前空間には [SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) から派生した一連のクラスが用意されています。これらのクラスは「[セーフ ハンドルの使用](#using-safe-handles)」にリストされています。 アンマネージ リソースを解放できるクラスが見つからない場合は、[SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) の独自のサブクラスを実装できます。 
 
* [IDisposable](xref:System.IDisposable) インターフェイスと追加の `Dispose(Boolean` メソッドを実装し、[Object.Finalize](xref:System.Object.Finalize) メソッドもオーバーライドします。 [IDisposable.Dispose](xref:System.IDisposable.Dispose) の実装が型のコンシューマーによって呼び出されなかった場合にアンマネージ リソースが破棄されるように、[Finalize](xref:System.Object.Finalize) をオーバーライドする必要があります。 前の項目で説明された推奨される方法を使用すると、[System.Runtime.InteropServices.SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) クラスが代わりにこれを実行します。 

[Dispose](xref:System.IDisposable.Dispose) メソッドが複数回呼び出される場合でも、例外をスローすることなく呼び出されるようにして、リソースが常に適切にクリーンアップされるようにする必要があります。 

[GC.KeepAlive](xref:System.GC.KeepAlive(System.Object)) メソッドのコード例では、再利用するオブジェクトのメンバーがまだ実行中の場合でも、ガベージ コレクションがファイナライザーを実行しようとします。 長い `Dispose` メソッドの最後に、[KeepAlive](xref:System.GC.KeepAlive(System.Object)) メソッドを呼び出すことをお勧めします。

## <a name="dispose-and-disposeboolean"></a>Dispose() と Dispose(Boolean)

[IDisposable](xref:System.IDisposable) インターフェイスでは、パラメーターのない [Dispose](xref:System.IDisposable.Dispose) メソッドを 1 つ実装する必要があります。 しかし、Dispose パターンでは 2 種類の `Dispose` メソッドを実装する必要があります。 

* public で非仮想 (Visual Basic では `NonInheritable`) の [IDisposable.Dispose](xref:System.IDisposable.Dispose) の実装。パラメーターはありません。

* protected で仮想 (Visual Basic では `Overridable`) の `Dispose` メソッド。シグネチャは次のとおりです。

  ```cs
  protected virtual void Dispose(bool disposing)
  ```

  ```vb
  Protected Overridable Sub Dispose(disposing As Boolean)
  ```

### <a name="the-dispose-overload"></a>Dispose() オーバーロード

この public で非仮想 (Visual Basic では `NonInheritable`)、パラメーターなしの `Dispose` メソッドは、型のコンシューマーによって呼び出されるため、その目的は、アンマネージ リソースを解放し、ファイナライザーが存在する場合、それを実行する必要がないことを示すことです。 このため、次のような標準的な実装があります。

```cs
public void Dispose()
{
   // Dispose of unmanaged resources.
   Dispose(true);
   // Suppress finalization.
   GC.SuppressFinalize(this);
}
```

```vb
Public Sub Dispose() _
           Implements IDisposable.Dispose
   ' Dispose of unmanaged resources.
   Dispose(True)
   ' Suppress finalization.
   GC.SuppressFinalize(Me)
End Sub
```

`Dispose` メソッドはオブジェクトのクリーンアップをすべて実行するため、ガベージ コレクターはもはやオブジェクトの [Object.Finalize](xref:System.Object.Finalize) のオーバーライドを呼び出す必要はありません。 そこで、[GC.SuppressFinalize](xref:System.GC.SuppressFinalize(System.Object)) メソッドを呼び出して、ガベージ コレクターによるファイナライザーの実行を抑制します。 型にファイナライザーがない場合、[SuppressFinalize](xref:System.GC.SuppressFinalize(System.Object)) を呼び出しても無効です。 アンマネージ リソースを解放する実際の作業は `Dispose` メソッドの 2 番目のオーバーロードによって実行されることに注意してください。

### <a name="the-disposeboolean-overload"></a>Dispose(Boolean) オーバーロード

2 番目のオーバーロードでは、*disposing* パラメーターは [Boolean](xref:System.Boolean) で、メソッドの呼び出し元が [Dispose](xref:System.IDisposable.Dispose) メソッドか (値は `true`)、それともファイナライザーか (値は `false`) を示します。 

メソッドの本体は 2 つのコード ブロックで構成されます。 

* アンマネージ リソースを解放するブロック。 このブロックは、*disposing* パラメーターの値に関係なく実行されます。 

* マネージ リソースを解放する条件付きブロック。 このブロックは、*disposing* の値が `true` の場合に実行されます。 解放するマネージ リソースには、次のオブジェクトを含めることができます。 

    **IDisposable を実装するマネージ オブジェクト** 条件付きブロックを使用して [Dispose](xref:System.IDisposable.Dispose) の実装を呼び出すことができます。 セーフ ハンドルを使用してアンマネージ リソースをラップしている場合は、ここで [SafeHandle.Dispose(Boolean](xref:System.Runtime.InteropServices.SafeHandle.Dispose(System.Boolean)) の実装を呼び出す必要があります。 

    **大量のメモリを消費するか、不足しているリソースを消費するマネージ オブジェクト。** これらのオブジェクトを `Dispose` メソッドで明示的に解放すると、ガベージ コレクターによって非確定的に解放される場合よりも迅速に解放されます。 


メソッドの呼び出し元がファイナライザーの場合 (つまり、*disposing* が `false` の場合)、アンマネージ リソースを解放するコードだけが実行されます。 ガベージ コレクターが終了処理の際にマネージ オブジェクトを破棄する順序は定義されていないため、値 `Dispose` を指定した `false` オーバーロードを呼び出すことで、既に解放されている可能性のあるマネージ リソースをファイナライザーが解放しようとすることを防止できます。 

## <a name="implementing-the-dispose-pattern-for-a-base-class"></a>基底クラスでの Dispose パターンの実装

基底クラスで Dispose パターンを実装する場合、以下の項目を用意する必要があります。 

> [!IMPORTANT]
> [IDisposable](xref:System.IDisposable) を実装し、`sealed` ではないすべてのベース クラスにこのパターンを実装してください。 
 
* `Dispose(Boolean)` メソッドを呼び出す [Dispose](xref:System.IDisposable.Dispose) の実装。 

* リソースを解放する実際の作業を実行する `Dispose(Boolean)` メソッド。 

* アンマネージ リソースをラップする [SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) から派生したクラス (推奨)、または、[Object.Finalize](xref:System.Object.Finalize) メソッドのオーバーライド。 [SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) クラスには、コーディングが不要なファイナライザーが用意されています。 

セーフ ハンドルを使用して基底クラスで Dispose パターンを実装する一般的なパターンを次に示します。 

```cs
using Microsoft.Win32.SafeHandles;
using System;
using System.Runtime.InteropServices;

class BaseClass : IDisposable
{
   // Flag: Has Dispose already been called?
   bool disposed = false;
   // Instantiate a SafeHandle instance.
   SafeHandle handle = new SafeFileHandle(IntPtr.Zero, true);

   // Public implementation of Dispose pattern callable by consumers.
   public void Dispose()
   { 
      Dispose(true);
      GC.SuppressFinalize(this);           
   }

   // Protected implementation of Dispose pattern.
   protected virtual void Dispose(bool disposing)
   {
      if (disposed)
         return; 

      if (disposing) {
         handle.Dispose();
         // Free any other managed objects here.
         //
      }

      // Free any unmanaged objects here.
      //
      disposed = true;
   }
}
```

```vb
Imports Microsoft.Win32.SafeHandles
Imports System.Runtime.InteropServices

Class BaseClass : Implements IDisposable
   ' Flag: Has Dispose already been called?
   Dim disposed As Boolean = False
   ' Instantiate a SafeHandle instance.
   Dim handle As SafeHandle = New SafeFileHandle(IntPtr.Zero, True)

   ' Public implementation of Dispose pattern callable by consumers.
   Public Sub Dispose() _
              Implements IDisposable.Dispose
      Dispose(True)
      GC.SuppressFinalize(Me)           
   End Sub

   ' Protected implementation of Dispose pattern.
   Protected Overridable Sub Dispose(disposing As Boolean)
      If disposed Then Return

      If disposing Then
         handle.Dispose()
         ' Free any other managed objects here.
         '
      End If

      ' Free any unmanaged objects here.
      '
      disposed = True
   End Sub
End Class
```

> [!NOTE] 
> 前の例では、[SafeFileHandle](xref:Microsoft.Win32.SafeHandles.SafeFileHandle) オブジェクトを使用してパターンを示しています。代わりに、[SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) から派生した任意のオブジェクトを使用することもできます。 例では、[SafeFileHandle](xref:Microsoft.Win32.SafeHandles.SafeFileHandle) オブジェクトを正しくインスタンス化していないことに注意してください。 
 
[Object.Finalize](xref:System.Object.Finalize) をオーバーライドして基底クラスで Dispose パターンを実装する一般的なパターンを次に示します。 

```cs
using System;

class BaseClass : IDisposable
{
   // Flag: Has Dispose already been called?
   bool disposed = false;

   // Public implementation of Dispose pattern callable by consumers.
   public void Dispose()
   { 
      Dispose(true);
      GC.SuppressFinalize(this);           
   }

   // Protected implementation of Dispose pattern.
   protected virtual void Dispose(bool disposing)
   {
      if (disposed)
         return; 

      if (disposing) {
         // Free any other managed objects here.
         //
      }

      // Free any unmanaged objects here.
      //
      disposed = true;
   }

   ~BaseClass()
   {
      Dispose(false);
   }
}
```

```vb
Class BaseClass : Implements IDisposable
   ' Flag: Has Dispose already been called?
   Dim disposed As Boolean = False

   ' Public implementation of Dispose pattern callable by consumers.
   Public Sub Dispose() _
              Implements IDisposable.Dispose
      Dispose(True)
      GC.SuppressFinalize(Me)           
   End Sub

   ' Protected implementation of Dispose pattern.
   Protected Overridable Sub Dispose(disposing As Boolean)
      If disposed Then Return

      If disposing Then
         ' Free any other managed objects here.
         '
      End If

      ' Free any unmanaged objects here.
      '
      disposed = True
   End Sub

   Protected Overrides Sub Finalize()
      Dispose(False)      
   End Sub
End Class
```

> [!NOTE]
> C# では、`destructor` を定義することで [Object.Finalize](xref:System.Object.Finalize) をオーバーライドします。 


## <a name="implementing-the-dispose-pattern-for-a-derived-class"></a>派生クラスでの Dispose パターンの実装

[IDisposable](xref:System.IDisposable) インターフェイスを実装するクラスから派生したクラスは、[IDisposable.Dispose](xref:System.IDisposable.Dispose) の基底クラスでの実装が派生クラスに継承されるため、[IDisposable](xref:System.IDisposable) を実装しないでください。 代わりに、派生クラスで Dispose パターンを実装するには、以下の項目を用意します。 

* 基底クラスのメソッドをオーバーライドして、派生クラスのリソースを解放する実際の作業を実行する `protected Dispose(Boolean)` メソッド。 このメソッドは、基底クラスの `Dispose(Boolean)` メソッドも呼び出して、それに *disposing* 引数の値として `true` を渡す必要があります。 

* アンマネージ リソースをラップする [SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) から派生したクラス (推奨)、または、[Object.Finalize](xref:System.Object.Finalize) メソッドのオーバーライド。 [SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) クラスには、コーディングが不要なファイナライザーが用意されています。 ファイナライザーを用意する場合は、*disposing* 引数を `false` として `Dispose(Boolean)` オーバーロードを呼び出す必要があります。 

セーフ ハンドルを使用して派生クラスで Dispose パターンを実装する一般的なパターンを次に示します。 

```cs
using Microsoft.Win32.SafeHandles;
using System;
using System.Runtime.InteropServices;

class DerivedClass : BaseClass
{
   // Flag: Has Dispose already been called?
   bool disposed = false;
   // Instantiate a SafeHandle instance.
   SafeHandle handle = new SafeFileHandle(IntPtr.Zero, true);

   // Protected implementation of Dispose pattern.
   protected override void Dispose(bool disposing)
   {
      if (disposed)
         return; 

      if (disposing) {
         handle.Dispose();
         // Free any other managed objects here.
         //
      }

      // Free any unmanaged objects here.
      //

      disposed = true;
      // Call base class implementation.
      base.Dispose(disposing);
   }
}
```

```vb
Imports Microsoft.Win32.SafeHandles
Imports System.Runtime.InteropServices

Class DerivedClass : Inherits BaseClass 
   ' Flag: Has Dispose already been called?
   Dim disposed As Boolean = False
   ' Instantiate a SafeHandle instance.
   Dim handle As SafeHandle = New SafeFileHandle(IntPtr.Zero, True)

   ' Protected implementation of Dispose pattern.
   Protected Overrides Sub Dispose(disposing As Boolean)
      If disposed Then Return

      If disposing Then
         handle.Dispose()
         ' Free any other managed objects here.
         '
      End If

      ' Free any unmanaged objects here.
      '
      disposed = True

      ' Call base class implementation.
      MyBase.Dispose(disposing)
   End Sub
End Class
```

> [!NOTE] 
> 前の例では、[SafeFileHandle](xref:Microsoft.Win32.SafeHandles.SafeFileHandle) オブジェクトを使用してパターンを示しています。代わりに、[SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) から派生した任意のオブジェクトを使用することもできます。 例では、[SafeFileHandle](xref:Microsoft.Win32.SafeHandles.SafeFileHandle) オブジェクトを正しくインスタンス化していないことに注意してください。 

[Object.Finalize](xref:System.Object.Finalize) をオーバーライドして派生クラスで Dispose パターンを実装する一般的なパターンを次に示します。

```cs
using System;

class DerivedClass : BaseClass
{
   // Flag: Has Dispose already been called?
   bool disposed = false;

   // Protected implementation of Dispose pattern.
   protected override void Dispose(bool disposing)
   {
      if (disposed)
         return; 

      if (disposing) {
         // Free any other managed objects here.
         //
      }

      // Free any unmanaged objects here.
      //
      disposed = true;

      // Call the base class implementation.
      base.Dispose(disposing);
   }

   ~DerivedClass()
   {
      Dispose(false);
   }
}
```

```vb
Class DerivedClass : Inherits BaseClass
   ' Flag: Has Dispose already been called?
   Dim disposed As Boolean = False

   ' Protected implementation of Dispose pattern.
   Protected Overrides Sub Dispose(disposing As Boolean)
      If disposed Then Return

      If disposing Then
         ' Free any other managed objects here.
         '
      End If

      ' Free any unmanaged objects here.
      '
      disposed = True

      ' Call the base class implementation.
      MyBase.Dispose(disposing)
   End Sub

   Protected Overrides Sub Finalize()
      Dispose(False)
   End Sub 
End Class
```

> [!NOTE]
> C# では、`destructor` を定義することで [Object.Finalize](xref:System.Object.Finalize) をオーバーライドします。

## <a name="using-safe-handles"></a>セーフ ハンドルの使用

オブジェクトのファイナライザーのコードを記述することは、正しく行わないと問題が発生する可能性がある複雑なタスクです。 そのため、ファイナライザーを実装するのではなく、[System.Runtime.InteropServices.SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) オブジェクトを構築することをお勧めします。

[System.Runtime.InteropServices.SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) クラスから派生したクラスは、処理を中断することなくハンドルの割り当てと解放を行うことで、オブジェクトの有効期間に関する問題を単純化します。 セーフ ハンドルは、アプリケーション ドメインのアンロード中に確実に実行されるクリティカル ファイナライザーを含んでいます。 [Microsoft.Win32.SafeHandles](xref:Microsoft.Win32.SafeHandles) 名前空間の次の派生クラスは、セーフ ハンドルを提供します。 

* ファイル、メモリ マップ ファイル、パイプのための [SafeFileHandle](xref:Microsoft.Win32.SafeHandles.SafeFileHandle)、[SafeMemoryMappedFileHandle](xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedFileHandle)、[SafePipeHandle](xref:Microsoft.Win32.SafeHandles.SafePipeHandle) クラス。 

* メモリ ビューのための [SafeMemoryMappedViewHandle](xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle) クラス。 

* 暗号の構成要素のための [SafeNCryptKeyHandle](https://msdn.microsoft.com/en-us/library/microsoft.win32.safehandles.safencryptkeyhandle(v=vs.110).aspx)、[SafeNCryptProviderHandle](https://msdn.microsoft.com/en-us/library/microsoft.win32.safehandles.safencryptproviderhandle(v=vs.110).aspx)、[SafeNCryptSecretHandle](https://msdn.microsoft.com/en-us/library/microsoft.win32.safehandles.safencryptsecrethandle(v=vs.110).aspx) クラス。

* レジストリ キーのための [SafeRegistryHandle](xref:Microsoft.Win32.SafeHandles.SafeRegistryHandle) クラス。 

* 待機ハンドルのための [SafeWaitHandle](xref:Microsoft.Win32.SafeHandles.SafeWaitHandle) クラス。 

## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-base-class"></a>セーフ ハンドルを使用した基底クラスでの Dispose パターンの実装

次の例は、セーフ ハンドルを使用してアンマネージ リソースをカプセル化する、基底クラス `DisposableStreamResource` での Dispose パターンを示します。 例では、[SafeFileHandle](xref:Microsoft.Win32.SafeHandles.SafeFileHandle) を使用して、開いているファイルを表す [Stream](xref:System.IO.Stream) オブジェクトをラップする `DisposableResource` クラスを定義しています。 `DisposableResource` メソッドには、ファイル ストリームの合計バイト数を返す `Size` プロパティも含まれています。 

```cs
using Microsoft.Win32.SafeHandles;
using System;
using System.IO;
using System.Runtime.InteropServices;

public class DisposableStreamResource : IDisposable
{
   // Define constants.
   protected const uint GENERIC_READ = 0x80000000;
   protected const uint FILE_SHARE_READ = 0x00000001;
   protected const uint OPEN_EXISTING = 3;
   protected const uint FILE_ATTRIBUTE_NORMAL = 0x80;
   protected IntPtr INVALID_HANDLE_VALUE = new IntPtr(-1);
   private const int INVALID_FILE_SIZE = unchecked((int) 0xFFFFFFFF);

   // Define Windows APIs.
   [DllImport("kernel32.dll", EntryPoint = "CreateFileW", CharSet = CharSet.Unicode)]
   protected static extern IntPtr CreateFile (
                                  string lpFileName, uint dwDesiredAccess, 
                                  uint dwShareMode, IntPtr lpSecurityAttributes, 
                                  uint dwCreationDisposition, uint dwFlagsAndAttributes, 
                                  IntPtr hTemplateFile);

   [DllImport("kernel32.dll")]
   private static extern int GetFileSize(SafeFileHandle hFile, out int lpFileSizeHigh);

   // Define locals.
   private bool disposed = false;
   private SafeFileHandle safeHandle; 
   private long bufferSize;
   private int upperWord;

   public DisposableStreamResource(string filename)
   {
      if (filename == null)
         throw new ArgumentNullException("The filename cannot be null.");
      else if (filename == "")
         throw new ArgumentException("The filename cannot be an empty string.");

      IntPtr handle = CreateFile(filename, GENERIC_READ, FILE_SHARE_READ,
                                 IntPtr.Zero, OPEN_EXISTING, FILE_ATTRIBUTE_NORMAL,
                                 IntPtr.Zero);
      if (handle != INVALID_HANDLE_VALUE)
         safeHandle = new SafeFileHandle(handle, true);
      else
         throw new FileNotFoundException(String.Format("Cannot open '{0}'", filename));

      // Get file size.
      bufferSize = GetFileSize(safeHandle, out upperWord); 
      if (bufferSize == INVALID_FILE_SIZE)
         bufferSize = -1;
      else if (upperWord > 0) 
         bufferSize = (((long)upperWord) << 32) + bufferSize;
   }

   public long Size 
   { get { return bufferSize; } }

   public void Dispose()
   {
      Dispose(true);
      GC.SuppressFinalize(this);
   }           

   protected virtual void Dispose(bool disposing)
   {
      if (disposed) return;

      // Dispose of managed resources here.
      if (disposing)
         safeHandle.Dispose();

      // Dispose of any unmanaged resources not wrapped in safe handles.

      disposed = true;
   }  
}
```

```vb
Imports Microsoft.Win32.SafeHandles
Imports System.IO

Public Class DisposableStreamResource : Implements IDisposable
   ' Define constants.
   Protected Const GENERIC_READ As UInteger = &H80000000ui
   Protected Const FILE_SHARE_READ As UInteger = &H0000000i
   Protected Const OPEN_EXISTING As UInteger = 3
   Protected Const FILE_ATTRIBUTE_NORMAL As UInteger = &H80
   Protected INVALID_HANDLE_VALUE As New IntPtr(-1)
   Private Const INVALID_FILE_SIZE As Integer = &HFFFFFFFF

   ' Define Windows APIs.
   Protected Declare Function CreateFile Lib "kernel32" Alias "CreateFileA" (
                                         lpFileName As String, dwDesiredAccess As UInt32, 
                                         dwShareMode As UInt32, lpSecurityAttributes As IntPtr, 
                                         dwCreationDisposition As UInt32, dwFlagsAndAttributes As UInt32, 
                                         hTemplateFile As IntPtr) As IntPtr
   Private Declare Function GetFileSize Lib "kernel32" (hFile As SafeFileHandle, 
                                                        ByRef lpFileSizeHigh As Integer) As Integer

   ' Define locals.
   Private disposed As Boolean = False
   Private safeHandle As SafeFileHandle 
   Private bufferSize As Long 
   Private upperWord As Integer

   Public Sub New(filename As String)
      If filename Is Nothing Then
         Throw New ArgumentNullException("The filename cannot be null.")
      Else If filename = ""
         Throw New ArgumentException("The filename cannot be an empty string.")
      End If

      Dim handle As IntPtr = CreateFile(filename, GENERIC_READ, FILE_SHARE_READ,
                                        IntPtr.Zero, OPEN_EXISTING, FILE_ATTRIBUTE_NORMAL,
                                        IntPtr.Zero)
      If handle <> INVALID_HANDLE_VALUE Then
         safeHandle = New SafeFileHandle(handle, True)
      Else
         Throw New FileNotFoundException(String.Format("Cannot open '{0}'", filename))
      End If

      ' Get file size.
      bufferSize = GetFileSize(safeHandle, upperWord) 
      If bufferSize = INVALID_FILE_SIZE Then
         bufferSize = -1
      Else If upperWord > 0 Then 
         bufferSize = (CLng(upperWord) << 32) + bufferSize
      End If     
   End Sub

   Public ReadOnly Property Size As Long
      Get
         Return bufferSize
      End Get
   End Property

   Public Sub Dispose() _
              Implements IDisposable.Dispose
      Dispose(True)
      GC.SuppressFinalize(Me)
   End Sub           

   Protected Overridable Sub Dispose(disposing As Boolean)
      If disposed Then Exit Sub

      ' Dispose of managed resources here.
      If disposing Then
         safeHandle.Dispose()
      End If

      ' Dispose of any unmanaged resources not wrapped in safe handles.

      disposed = True
   End Sub  
End Class
```

## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-derived-class"></a>セーフ ハンドルを使用した派生クラスでの Dispose パターンの実装

次の例は、前の例で挙げた `DisposableStreamResource2` クラスを継承した派生クラス `DisposableStreamResource` での Dispose パターンを示します。 このクラスは `WriteFileInfo` メソッドを追加し、[SafeFileHandle](xref:Microsoft.Win32.SafeHandles.SafeFileHandle) オブジェクトを使用して書き込み可能ファイル ハンドルをラップしています。 

```cs
using Microsoft.Win32.SafeHandles;
using System;
using System.IO;
using System.Runtime.InteropServices;
using System.Threading;

public class DisposableStreamResource2 : DisposableStreamResource
{
   // Define additional constants.
   protected const uint GENERIC_WRITE = 0x40000000; 
   protected const uint OPEN_ALWAYS = 4;

   // Define additional APIs.
   [DllImport("kernel32.dll")]   
   protected static extern bool WriteFile(
                                SafeFileHandle safeHandle, string lpBuffer, 
                                int nNumberOfBytesToWrite, out int lpNumberOfBytesWritten,
                                IntPtr lpOverlapped);

   // Define locals.
   private bool disposed = false;
   private string filename;
   private bool created = false;
   private SafeFileHandle safeHandle;

   public DisposableStreamResource2(string filename) : base(filename)
   {
      this.filename = filename;
   }

   public void WriteFileInfo()
   { 
      if (! created) {
         IntPtr hFile = CreateFile(xref:".\FileInfo.txt", GENERIC_WRITE, 0, 
                                   IntPtr.Zero, OPEN_ALWAYS, 
                                   FILE_ATTRIBUTE_NORMAL, IntPtr.Zero);
         if (hFile != INVALID_HANDLE_VALUE)
            safeHandle = new SafeFileHandle(hFile, true);
         else
            throw new IOException("Unable to create output file.");

         created = true;
      }

      string output = String.Format("{0}: {1:N0} bytes\n", filename, Size);
      int bytesWritten;
      bool result = WriteFile(safeHandle, output, output.Length, out bytesWritten, IntPtr.Zero);                                     
   }

   protected new virtual void Dispose(bool disposing)
   {
      if (disposed) return;

      // Release any managed resources here.
      if (disposing)
         safeHandle.Dispose();

      disposed = true;

      // Release any unmanaged resources not wrapped by safe handles here.

      // Call the base class implementation.
      base.Dispose(true);
   }
}
```

```vb
Imports Microsoft.Win32.SafeHandles
Imports System.IO

Public Class DisposableStreamResource2 : Inherits DisposableStreamResource
   ' Define additional constants.
   Protected Const GENERIC_WRITE As Integer = &H40000000 
   Protected Const OPEN_ALWAYS As Integer = 4

   ' Define additional APIs.
   Protected Declare Function WriteFile Lib "kernel32.dll" (
                              safeHandle As SafeFileHandle, lpBuffer As String, 
                              nNumberOfBytesToWrite As Integer, ByRef lpNumberOfBytesWritten As Integer,
                              lpOverlapped As Object) As Boolean

   ' Define locals.
   Private disposed As Boolean = False
   Private filename As String
   Private created As Boolean = False
   Private safeHandle As SafeFileHandle

   Public Sub New(filename As String)
      MyBase.New(filename)
      Me.filename = filename
   End Sub

   Public Sub WriteFileInfo() 
      If Not created Then
         Dim hFile As IntPtr = CreateFile(".\FileInfo.txt", GENERIC_WRITE, 0, 
                                          IntPtr.Zero, OPEN_ALWAYS, 
                                          FILE_ATTRIBUTE_NORMAL, IntPtr.Zero)
         If hFile <> INVALID_HANDLE_VALUE Then
            safeHandle = New SafeFileHandle(hFile, True)
         Else
            Throw New IOException("Unable to create output file.")
         End If
         created = True
      End If
      Dim output As String = String.Format("{0}: {1:N0} bytes {2}", filename, Size, 
                                           vbCrLf)
      WriteFile(safeHandle, output, output.Length, 0&, Nothing)                                     
   End Sub

   Protected Overloads Overridable Sub Dispose(disposing As Boolean)
      If disposed Then Exit Sub

      ' Release any managed resources here.
      If disposing Then
         safeHandle.Dispose()
      End If

      disposed = True
      ' Release any unmanaged resources not wrapped by safe handles here.

      ' Call the base class implementation.
      MyBase.Dispose(True)
   End Sub
End Class
```

## <a name="see-also"></a>関連項目

[SuppressFinalize](xref:System.GC.SuppressFinalize(System.Object))

[IDisposable](xref:System.IDisposable)

[IDisposable.Dispose](xref:System.IDisposable.Dispose)

[Microsoft.Win32.SafeHandles](xref:Microsoft.Win32.SafeHandles)

[System.Runtime.InteropServices.SafeHandle](xref:System.Runtime.InteropServices.SafeHandle)

[IDisposable.Dispose](xref:System.IDisposable.Dispose)



<!--HONumber=Nov16_HO1-->


