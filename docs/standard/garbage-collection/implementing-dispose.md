---
title: "Dispose メソッドの実装 | Microsoft Docs"
ms.custom: ""
ms.date: "04/07/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Dispose メソッド"
  - "ガベージ コレクション、Dispose メソッド"
ms.assetid: eb4e1af0-3b48-4fbc-ad4e-fc2f64138bf9
caps.latest.revision: 44
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 44
---
# Dispose メソッドの実装
アプリケーションによって使用されるアンマネージ リソースを解放するための <xref:System.IDisposable.Dispose%2A> メソッドを実装します。 .NET Framework ガベージ コレクターは、アンマネージ メモリの割り当てや解放を行いません。  
  
 呼ばれる、オブジェクトを破棄するパターン、 [dispose パターン](../../../docs/standard/design-guidelines/dispose-pattern.md)オブジェクトの有効期間に順番が付けられます。 Dispose パターンは、ファイルおよびパイプ ハンドル、レジストリ ハンドル、待機ハンドル、アンマネージ メモリ ブロックのポインターなど、アンマネージ リソースにアクセスするオブジェクトでのみ使用されます。 これは、使用されていないマネージ オブジェクトの解放にはガベージ コレクターが非常に有効ですが、アンマネージ オブジェクトは解放できないためです。  
  
 Dispose パターンには&2; 種類あります。  
  
-   型で使用する各アンマネージ リソースをセーフ ハンドル (つまり、<xref:System.Runtime.InteropServices.SafeHandle?displayProperty=fullName> から派生したクラス) でラップします。 この場合、<xref:System.IDisposable> インターフェイスと追加の `Dispose(Boolean)` メソッドを実装します。 これは推奨される方法で、<xref:System.Object.Finalize%2A?displayProperty=fullName> メソッドをオーバーライドする必要がありません。  
  
    > [!NOTE]
    >  <xref:Microsoft.Win32.SafeHandles?displayProperty=fullName> 名前空間には <xref:System.Runtime.InteropServices.SafeHandle> から派生した一連のクラスが用意されています。これらのクラスは「[セーフ ハンドルの使用](#SafeHandles)」にリストされています。 アンマネージ リソースを解放できるクラスが見つからない場合は、<xref:System.Runtime.InteropServices.SafeHandle> の独自のサブクラスを実装できます。  
  
-   実装する、 <xref:System.IDisposable>インターフェイスと追加`Dispose(Boolean)`メソッドもオーバーライド、 <xref:System.Object.Finalize%2A?displayProperty=fullName>メソッドです。 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> の実装が型のコンシューマーによって呼び出されなかった場合にアンマネージ リソースが破棄されるように、<xref:System.Object.Finalize%2A> をオーバーライドする必要があります。 前の項目で説明された推奨される方法を使用すると、<xref:System.Runtime.InteropServices.SafeHandle?displayProperty=fullName> クラスが代わりにこれを実行します。  
  
 <xref:System.IDisposable.Dispose%2A> メソッドが複数回呼び出される場合でも、例外をスローすることなく呼び出されるようにして、リソースが常に適切にクリーンアップされるようにする必要があります。  
  
> [!IMPORTANT]
>  C++ プログラマならを実装していない、 <xref:System.IDisposable.Dispose%2A>メソッドです。 「デストラクターとファイナライザー」セクションの指示に従って、代わりに、[する方法: 定義消費クラスと構造体 (C + +/CLI)](../Topic/How%20to:%20Define%20and%20Consume%20Classes%20and%20Structs%20\(C++-CLI\).md)します。 以降、.NET Framework 2.0 では、C++ コンパイラはリソースの確定的な破棄をサポートしの直接の実装を許可しない、 <xref:System.IDisposable.Dispose%2A>メソッドです。  
  
 <xref:System.GC.KeepAlive%2A?displayProperty=fullName> メソッドのコード例では、再利用するオブジェクトのメンバーがまだ実行中の場合でも、ガベージ コレクションがファイナライザーを実行しようとします。 呼び出すことをお勧めします<xref:System.GC.KeepAlive%2A>メソッド、時間がかかるの最後に<xref:System.IDisposable.Dispose%2A>メソッドです。  
  
<a name="Dispose2"></a>   
## <a name="dispose-and-disposeboolean"></a>Dispose() と Dispose(Boolean)  
 <xref:System.IDisposable> インターフェイスでは、パラメーターのない <xref:System.IDisposable.Dispose%2A> メソッドを&1; つ実装する必要があります。 しかし、Dispose パターンでは&2; 種類の `Dispose` メソッドを実装する必要があります。  
  
-   public で非仮想 (Visual Basic では `NonInheritable`) の <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> の実装。パラメーターはありません。  
  
-   protected で仮想 (Visual Basic では `Overridable`) の `Dispose` メソッド。シグネチャは次のとおりです。  
  
     [!code-csharp[Conceptual.Disposable#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#8)]
     [!code-vb[Conceptual.Disposable#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#8)]  
  
### <a name="the-dispose-overload"></a>Dispose() オーバーロード  
 この public で非仮想 (Visual Basic では `NonInheritable`)、パラメーターなしの `Dispose` メソッドは、型のコンシューマーによって呼び出されるため、その目的は、アンマネージ リソースを解放し、ファイナライザーが存在する場合、それを実行する必要がないことを示すことです。 このため、次のような標準的な実装があります。  
  
 [!code-csharp[Conceptual.Disposable#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#7)]
 [!code-vb[Conceptual.Disposable#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#7)]  
  
 `Dispose` メソッドはオブジェクトのクリーンアップをすべて実行するため、ガベージ コレクターはもはやオブジェクトの <xref:System.Object.Finalize%2A?displayProperty=fullName> のオーバーライドを呼び出す必要はありません。 そのため、呼び出しを<xref:System.GC.SuppressFinalize%2A>メソッドにより、ガベージ コレクターによるファイナライザーの実行します。 型にファイナライザーの呼び出しにないかどうかは<xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>も何も起こりません。 アンマネージ リソースを解放する実際の作業は `Dispose` メソッドの&2; 番目のオーバーロードによって実行されることに注意してください。  
  
### <a name="the-disposeboolean-overload"></a>Dispose(Boolean) オーバーロード  
 2 番目のオーバー ロードでは、`disposing`パラメーターは、<xref:System.Boolean>メソッドの呼び出し元となるかどうかを示す、 <xref:System.IDisposable.Dispose%2A>メソッド (その値は`true`) それともファイナライザーか (その値は`false`)。  
  
 メソッドの本体は&2; つのコード ブロックで構成されます。  
  
-   アンマネージ リソースを解放するブロック。 このブロックは、`disposing` パラメーターの値に関係なく実行されます。  
  
-   マネージ リソースを解放する条件付きブロック。 このブロックは、`disposing` の値が `true` の場合に実行されます。 解放するマネージ リソースには、次のオブジェクトを含めることができます。  
  
     **実装するマネージ オブジェクト<xref:System.IDisposable>します。**  
     条件付きブロックを使用して <xref:System.IDisposable.Dispose%2A> の実装を呼び出すことができます。 呼び出す必要がありますをアンマネージ リソースをラップするセーフ ハンドルを使用した場合、 <xref:System.Runtime.InteropServices.SafeHandle.Dispose%28System.Boolean%29?displayProperty=fullName>ここでの実装です。  
  
     **大量のメモリを消費するか、不足しているリソースを消費するマネージ オブジェクト。**  
     これらのオブジェクトを `Dispose` メソッドで明示的に解放すると、ガベージ コレクターによって非確定的に解放される場合よりも迅速に解放されます。  
  
 メソッドの呼び出し元がファイナライザーの場合 (つまり、`disposing` が `false` の場合)、アンマネージ リソースを解放するコードだけが実行されます。 ガベージ コレクターが終了処理の際にマネージ オブジェクトを破棄する順序は定義されていないため、値 `Dispose` を指定した `false` オーバーロードを呼び出すことで、既に解放されている可能性のあるマネージ リソースをファイナライザーが解放しようとすることを防止できます。  
  
## <a name="implementing-the-dispose-pattern-for-a-base-class"></a>基底クラスでの Dispose パターンの実装  
 基底クラスで Dispose パターンを実装する場合、以下の項目を用意する必要があります。  
  
> [!IMPORTANT]
>  すべての基底クラスを実装するには、このパターンを実装する必要があります<xref:System.IDisposable>されない`sealed`(`NotInheritable` Visual Basic で)。  
  
-   `Dispose(Boolean)` メソッドを呼び出す <xref:System.IDisposable.Dispose%2A> の実装。  
  
-   リソースを解放する実際の作業を実行する `Dispose(Boolean)` メソッド。  
  
-   アンマネージ リソースをラップする <xref:System.Runtime.InteropServices.SafeHandle> から派生したクラス (推奨)、または、<xref:System.Object.Finalize%2A?displayProperty=fullName> メソッドのオーバーライド。 <xref:System.Runtime.InteropServices.SafeHandle> クラスには、コーディングが不要なファイナライザーが用意されています。  
  
 セーフ ハンドルを使用して基底クラスで Dispose パターンを実装する一般的なパターンを次に示します。  
  
 [!code-csharp[System.IDisposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base1.cs#3)]
 [!code-vb[System.IDisposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base1.vb#3)]  
  
> [!NOTE]
>  前の例では、<xref:Microsoft.Win32.SafeHandles.SafeFileHandle> オブジェクトを使用してパターンを示しています。代わりに、<xref:System.Runtime.InteropServices.SafeHandle> から派生した任意のオブジェクトを使用することもできます。 例では、<xref:Microsoft.Win32.SafeHandles.SafeFileHandle> オブジェクトを正しくインスタンス化していないことに注意してください。  
  
 <xref:System.Object.Finalize%2A?displayProperty=fullName> をオーバーライドして基底クラスで Dispose パターンを実装する一般的なパターンを次に示します。  
  
 [!code-csharp[System.IDisposable#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base2.cs#5)]
 [!code-vb[System.IDisposable#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base2.vb#5)]  
  
> [!NOTE]
>  オーバーライドする、C# の場合は、 <xref:System.Object.Finalize%2A?displayProperty=fullName>定義することで、[デストラクター](../Topic/Destructors%20\(C%23%20Programming%20Guide\).md)します。  
  
## <a name="implementing-the-dispose-pattern-for-a-derived-class"></a>派生クラスでの Dispose パターンの実装  
 <xref:System.IDisposable> インターフェイスを実装するクラスから派生したクラスは、<xref:System.IDisposable.Dispose%2A?displayProperty=fullName> の基底クラスでの実装が派生クラスに継承されるため、<xref:System.IDisposable> を実装しないでください。 代わりに、派生クラスで Dispose パターンを実装するには、以下の項目を用意します。  
  
-   基底クラスのメソッドをオーバーライドして、派生クラスのリソースを解放する実際の作業を実行する `protected``Dispose(Boolean)` メソッド。 このメソッドは、基底クラスの `Dispose(Boolean)` メソッドも呼び出して、それに `true` 引数の値として `disposing` を渡す必要があります。  
  
-   アンマネージ リソースをラップする <xref:System.Runtime.InteropServices.SafeHandle> から派生したクラス (推奨)、または、<xref:System.Object.Finalize%2A?displayProperty=fullName> メソッドのオーバーライド。 <xref:System.Runtime.InteropServices.SafeHandle> クラスには、コーディングが不要なファイナライザーが用意されています。 ファイナライザーを用意する場合は、`Dispose(Boolean)` 引数を `disposing` として `false` オーバーロードを呼び出す必要があります。  
  
 セーフ ハンドルを使用して派生クラスで Dispose パターンを実装する一般的なパターンを次に示します。  
  
 [!code-csharp[System.IDisposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived1.cs#4)]
 [!code-vb[System.IDisposable#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived1.vb#4)]  
  
> [!NOTE]
>  前の例では、<xref:Microsoft.Win32.SafeHandles.SafeFileHandle> オブジェクトを使用してパターンを示しています。代わりに、<xref:System.Runtime.InteropServices.SafeHandle> から派生した任意のオブジェクトを使用することもできます。 例では、<xref:Microsoft.Win32.SafeHandles.SafeFileHandle> オブジェクトを正しくインスタンス化していないことに注意してください。  
  
 <xref:System.Object.Finalize%2A?displayProperty=fullName> をオーバーライドして派生クラスで Dispose パターンを実装する一般的なパターンを次に示します。  
  
 [!code-csharp[System.IDisposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived2.cs#6)]
 [!code-vb[System.IDisposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived2.vb#6)]  
  
> [!NOTE]
>  オーバーライドする、C# の場合は、 <xref:System.Object.Finalize%2A?displayProperty=fullName>定義することで、[デストラクター](../Topic/Destructors%20\(C%23%20Programming%20Guide\).md)します。  
  
<a name="SafeHandles"></a>   
## <a name="using-safe-handles"></a>セーフ ハンドルの使用  
 オブジェクトのファイナライザーのコードを記述することは、正しく行わないと問題が発生する可能性がある複雑なタスクです。 そのため、ファイナライザーを実装するのではなく、<xref:System.Runtime.InteropServices.SafeHandle?displayProperty=fullName> オブジェクトを構築することをお勧めします。  
  
 <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=fullName> クラスから派生したクラスは、処理を中断することなくハンドルの割り当てと解放を行うことで、オブジェクトの有効期間に関する問題を単純化します。 セーフ ハンドルは、アプリケーション ドメインのアンロード中に確実に実行されるクリティカル ファイナライザーを含んでいます。 セーフ ハンドルを使用する利点の詳細については、次を参照してください。 <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=fullName>します。 <xref:Microsoft.Win32.SafeHandles> 名前空間の次の派生クラスは、セーフ ハンドルを提供します。  
  
-   ファイル、メモリ マップ ファイル、パイプのための <xref:Microsoft.Win32.SafeHandles.SafeFileHandle>、<xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedFileHandle>、<xref:Microsoft.Win32.SafeHandles.SafePipeHandle> クラス。  
  
-   メモリ ビューのための <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> クラス。  
  
-   暗号の構成要素のための <xref:Microsoft.Win32.SafeHandles.SafeNCryptKeyHandle>、<xref:Microsoft.Win32.SafeHandles.SafeNCryptProviderHandle>、<xref:Microsoft.Win32.SafeHandles.SafeNCryptSecretHandle> クラス。  
  
-   レジストリ キーのための <xref:Microsoft.Win32.SafeHandles.SafeRegistryHandle> クラス。  
  
-   待機ハンドルのための <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> クラス。  
  
<a name="base"></a>   
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-base-class"></a>セーフ ハンドルを使用した基底クラスでの Dispose パターンの実装  
 次の例は、セーフ ハンドルを使用してアンマネージ リソースをカプセル化する、基底クラス `DisposableStreamResource` での Dispose パターンを示します。 例では、<xref:Microsoft.Win32.SafeHandles.SafeFileHandle> を使用して、開いているファイルを表す <xref:System.IO.Stream> オブジェクトをラップする `DisposableResource` クラスを定義しています。 `DisposableResource` メソッドには、ファイル ストリームの合計バイト数を返す `Size` プロパティも含まれています。  
  
 [!code-csharp[Conceptual.Disposable#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/base1.cs#9)]
 [!code-vb[Conceptual.Disposable#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/base1.vb#9)]  
  
<a name="derived"></a>   
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-derived-class"></a>セーフ ハンドルを使用した派生クラスでの Dispose パターンの実装  
 次の例は、前の例で挙げた `DisposableStreamResource2` クラスを継承した派生クラス `DisposableStreamResource` での Dispose パターンを示します。 このクラスは `WriteFileInfo` メソッドを追加し、<xref:Microsoft.Win32.SafeHandles.SafeFileHandle> オブジェクトを使用して書き込み可能ファイル ハンドルをラップしています。  
  
 [!code-csharp[Conceptual.Disposable#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/derived1.cs#10)]
 [!code-vb[Conceptual.Disposable#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/derived1.vb#10)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.GC.SuppressFinalize%2A>   
 <xref:System.IDisposable>   
 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>   
 <xref:Microsoft.Win32.SafeHandles>   
 <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=fullName>   
 <xref:System.Object.Finalize%2A?displayProperty=fullName>   
 [方法: クラスと構造体定義および使用 (C + +/CLI)](../Topic/How%20to:%20Define%20and%20Consume%20Classes%20and%20Structs%20\(C++-CLI\).md)   
 [Dispose パターン](../../../docs/standard/design-guidelines/dispose-pattern.md)