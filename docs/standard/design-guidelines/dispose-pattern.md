---
title: "Dispose パターン | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Dispose メソッド"
  - "クラス ライブラリ デザインのガイドライン [.NET Framework] Dispose メソッド"
  - "クラス ライブラリ デザインのガイドライン [.NET Framework] Finalize メソッド"
  - "Dispose メソッド名をカスタマイズします。"
  - "Finalize メソッド"
ms.assetid: 31a6c13b-d6a2-492b-9a9f-e5238c983bcb
caps.latest.revision: 22
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 22
---
# Dispose パターン
すべてのプログラムは、それらの実行の進行中にメモリ、システムのハンドル、またはデータベース接続など、1 つまたは複数のシステム リソースを取得します。 開発者である、取得、使用後に解放する必要があるために、このようなシステム リソースの使用に注意してください。  
  
 CLR では、自動メモリ管理がサポートされています。 管理されるメモリ \(c\# 演算子を使用して割り当てられたメモリ `new`\) 明示的に解放する必要はありません。 ガベージ コレクター \(GC\) によって自動的に解放されます。 これにより開発者のメモリを解放して難しい面倒な作業から解放されは、.NET Framework によって提供される優れた生産性向上のための主な理由の 1 つでした。  
  
 残念ながら、マネージ メモリは、さまざまな種類のシステム リソースの 1 つです。 ただし、マネージ メモリ以外のリソースは明示的に解放する必要あるし、アンマネージ リソースと呼びます。 GC はありませんされたこのようなアンマネージ リソースを管理する開発者の手にアンマネージ リソースを管理する責任があることを意味します。  
  
 CLR では、アンマネージ リソースを解放するときにいくつかのヘルプを提供します。<xref:System.Object?displayProperty=fullName> 仮想メソッドを宣言 <xref:System.Object.Finalize%2A> \(ファイナライザーとも呼ばれます\)、オブジェクトのメモリが GC によって回収され、上書きして、アンマネージ リソースを解放する前に、GC によって呼び出されます。 ファイナライザーのオーバーライドの種類は、ファイナライズ可能な型と呼ばれます。  
  
 ファイナライザーはクリーンアップの一部のシナリオで効果的なは、2 つの重要な欠点があります。  
  
-   GC はコレクションの対象オブジェクトを検出すると、ファイナライザーが呼び出されます。 これは、不定一定時間、リソースは必要ありません後に行われます。 開発者がでしたか、リソースおよびリソースが実際には、ファイナライザーで解放と時間を解放するまでの遅延は、リソースは \(大規模なアンマネージ メモリ バッファーなど\) の使用にコストがかかる場合や、多くの不足しているリソース \(リソースを簡単に使い果たされることができます\) を取得するプログラムで受け入れられない可能性があります。  
  
-   CLR は、ファイナライザーを呼び出す必要がある場合は、次の回ガベージ コレクション \(コレクションの間で実行するファイナライザー\) のするまで、オブジェクトのメモリのコレクションを延期にする必要があります。 これは、オブジェクトのメモリ \(およびすべてのオブジェクトを参照\) が、長期間に解放されないことを意味します。  
  
 そのため、ファイナライザーでのみ証明書利用者不適切となる多くのシナリオが不足しているリソースを処理する場合は、アンマネージ リソースをできるだけ早く再利用する必要がある場合または高パフォーマンスの高いシナリオがこれで、追加した GC オーバーヘッドの終了処理は許容されません。  
  
 フレームワークは、提供、 <xref:System.IDisposable?displayProperty=fullName> インターフェイスが必要でないと、すぐには、アンマネージ リソースを解放する手動の方法を開発者に提供するために実装する必要があります。 また、提供、 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> するように、GC が知ることができるメソッド、オブジェクトは手動で破棄され、その場合、オブジェクトのメモリを再要求できる前、終了する必要はありません。 実装する型、 `IDisposable` インターフェイスを破棄できる型と呼びます。  
  
 Dispose パターンの目的は、使用状況とファイナライザーの実装を標準化して、 `IDisposable` インターフェイスです。  
  
 パターンの主な動機がの実装の複雑さを軽減するには、 <xref:System.Object.Finalize%2A> と <xref:System.IDisposable.Dispose%2A> メソッドです。 複雑なメソッドがいくつかのコード パスが \(相違点は後で説明\) を共有するという事実に由来します。 さらに、確定的なリソース管理のための言語サポートの進化に関連するパターンの一部の要素の歴史的な理由があります。  
  
 **✓ は** 破棄可能な型のインスタンスを含む型の Dispose の基本的なパターンを実装します。 参照してください、 [基本的な Dispose パターン](#basic_pattern) セクションについては、基本的なパターンです。  
  
 型が破棄可能なその他のオブジェクトの有効期間を担当する場合は、開発者にも、それらを破棄する方法必要があります。 コンテナーを使用して `Dispose` メソッドは、これを可能にする便利な方法です。  
  
 **✓ は** 基本的な Dispose パターンを実装し、保持しているリソースに明示的に解放する必要があると、ファイナライザーを持たない型にファイナライザーを提供します。  
  
 たとえば、このパターンは、アンマネージ メモリ バッファーを格納する型で実装する必要があります。[ファイナライズ可能な型](#finalizable_types) ファイナライザーを実装する関連のガイドラインについて説明します。  
  
 **✓ を検討してください** クラス自体を保持しないことは、アンマネージ リソースまたは破棄可能なオブジェクトはサブタイプがある可能性が、基本的な Dispose パターンを実装します。  
  
 これの良い例は、 <xref:System.IO.Stream?displayProperty=fullName> クラスです。 すべてのリソースを保持しないする抽象基本クラスが、そのサブクラスのほとんどはし、このため、このパターンを実装します。  
  
<a name="basic_pattern"></a>   
## 基本的な Dispose パターン  
 パターンの基本的な実装には、実装が含まれます、 `System.IDisposable` インターフェイスと宣言する、 `Dispose(bool)` 間で共有するすべてのリソースのクリーンアップ ロジックを実装するメソッド、 `Dispose` メソッドと省略可能な終了します。  
  
 次の例は、基本的なパターンの単純な実装を示しています。  
  
```  
public class DisposableResourceHolder : IDisposable {  
  
    private SafeHandle resource; // handle to a resource  
  
    public DisposableResourceHolder(){  
        this.resource = ... // allocates the resource  
    }  
  
    public void Dispose(){  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
  
    protected virtual void Dispose(bool disposing){  
        if (disposing){  
            if (resource!= null) resource.Dispose();  
        }  
    }  
}  
```  
  
 ブール型パラメーター `disposing` からメソッドが呼び出されたかどうかを示す、 `IDisposable.Dispose` 実装またはファイナライザーからです。`Dispose(bool)` 実装は、その他の参照オブジェクト \(前のサンプルのリソース フィールドなど\) にアクセスする前に、パラメーターを確認する必要があります。 このようなオブジェクトから、メソッドが呼び出されたときにのみアクセスできる、 `IDisposable.Dispose` 実装 \(ときに、 `disposing` パラメーターが true に等しい\)。 メソッドは、ファイナライザーから呼び出される場合 \(`disposing` は false\)、その他のオブジェクトにアクセスしないようにします。 理由は、オブジェクトが予期しない順序で完了処理され、そのため、またはその依存関係のいずれかが既にファイナライズされていることです。  
  
 また、このセクションでは、Dispose パターンを実装しない基数を持つクラスに適用されます。 既にパターンを実装するクラスから継承している場合はオーバーライドするだけで、 `Dispose(bool)` 追加のリソースのクリーンアップ ロジックを提供します。  
  
 **✓ は** 宣言保護された仮想 void `Dispose(bool disposing)` アンマネージ リソースの解放に関連するすべてのロジックを一元化するメソッドです。  
  
 リソースのクリーンアップをすべては、このメソッドで発生する必要があります。 メソッドは、両方のファイナライザーから呼び出されると、 `IDisposable.Dispose` メソッドです。 パラメーターは、ファイナライザーの内部から呼び出されている場合は false になります。 終了処理中に実行されるコードは、ファイナライズ可能なその他のオブジェクトにアクセスしていないことを確認することを使用してください。 ファイナライザーを実装の詳細は、次のセクションで記述されます。  
  
```  
protected virtual void Dispose(bool disposing){  
    if (disposing){  
        if (resource!= null) resource.Dispose();  
    }  
}  
```  
  
 **✓ は** 実装、 `IDisposable` を単純に呼び出してインターフェイス `Dispose(true)` 続けて `GC.SuppressFinalize(this)`します。  
  
 呼び出し `SuppressFinalize` 場合にのみ発生 `Dispose(true)` 正常に実行されます。  
  
```  
public void Dispose(){  
    Dispose(true);  
    GC.SuppressFinalize(this);  
}  
```  
  
 **X のしないで** パラメーターなしで行う `Dispose` 仮想メソッドです。  
  
 `Dispose(bool)` メソッドは、1 つのサブクラスによってオーバーライドする必要があります。  
  
```  
// bad design  
public class DisposableResourceHolder : IDisposable {  
    public virtual void Dispose(){ ... }  
    protected virtual void Dispose(bool disposing){ ... }  
}  
  
// good design  
public class DisposableResourceHolder : IDisposable {  
    public void Dispose(){ ... }  
    protected virtual void Dispose(bool disposing){ ... }  
}  
```  
  
 **X のしないで** のすべてのオーバー ロードを宣言、 `Dispose` メソッド以外の `Dispose()` と `Dispose(bool)`です。  
  
 `Dispose` このパターンを体系化し、実装者、ユーザー、およびコンパイラの間で混乱を回避するために予約語を考慮必要があります。 一部の言語は、特定の種類に自動的にこのパターンを実装することもできます。  
  
 **✓ は** を許可する、 `Dispose(bool)` に複数回呼び出されるメソッド。 メソッドは、最初に呼び出した後何もしないこともできます。  
  
```  
public class DisposableResourceHolder : IDisposable {  
  
    bool disposed = false;  
  
    protected virtual void Dispose(bool disposing){  
        if(disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 **X 回避** 内から例外がスロー `Dispose(bool)` 限り重要な状況で格納しているプロセスが破損しています \(リークするなどの共有状態の整合性がありません。\)。  
  
 ユーザーが期待するへの呼び出し `Dispose` 例外は発生しません。  
  
 場合 `Dispose` 例外を発生させることが、さらに finally ブロックのクリーンアップ ロジックは実行されません。 この問題を回避するは、ユーザーはすべての呼び出しをラップする必要が `Dispose` \(内で、finally ブロック\!\) try ブロックで非常に複雑なクリーンアップのハンドラーにつながります。 実行されている場合、 `Dispose(bool disposing)` メソッド、破棄が false の場合も例外をスローさせることはありません。 そうにより、ファイナライザーのコンテキスト内に実行する場合、プロセスは終了します。  
  
 **✓ は** スロー、 <xref:System.ObjectDisposedException> すべてのメンバーのオブジェクトが破棄された後に使用できないからです。  
  
```  
public class DisposableResourceHolder : IDisposable {  
    bool disposed = false;  
    SafeHandle resource; // handle to a resource  
  
    public void DoSomething(){  
           if(disposed) throw new ObjectDisposedException(...);  
        // now call some native methods using the resource   
            ...  
    }  
    protected virtual void Dispose(bool disposing){  
        if(disposed) return;  
        // cleanup  
        ...  
        disposed = true;  
    }  
}  
```  
  
 **✓ を検討してください** メソッドを提供する `Close()`, に加え、 `Dispose()`, 、領域に一般的な用語が閉じるかどうか。  
  
 その場合であることが重要、 `Close` 実装と同じ `Dispose` を実装することを検討してください、 `IDisposable.Dispose` メソッドに明示的にします。  
  
```  
public class Stream : IDisposable {  
    IDisposable.Dispose(){  
        Close();  
    }  
    public void Close(){  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
<a name="finalizable_types"></a>   
## ファイナライズ可能な型  
 ファイナライズ可能な型はファイナライザーをオーバーライドし、\[ファイナライズ コード パスを提供することによって、基本的な Dispose パターンを拡張する型は、 `Dispose(bool)` メソッドです。  
  
 ファイナライザーは、主な理由は、実行中に、システムの状態に関する \(通常は有効な\) 仮定をすることはできません、正しく実装する非常に困難です。 次のガイドラインは、慎重に検討に考慮する必要があります。  
  
 しないようにだけに適用のガイドラインに注意してください、 `Finalize` メソッド、ファイナライザーがコードから呼び出されます。 つまり、ロジック内で実行されますが、基本的な Dispose パターン定義済みの場合 `Dispose(bool disposing)` ときに、 `disposing` パラメーターを false にします。  
  
 基本クラス既にファイナライズ可能なは、基本的な Dispose パターンを実装オーバーライドしないでください `Finalize` 再度します。 だけオーバーライドする代わりに、 `Dispose(bool)` 追加のリソースのクリーンアップ ロジックを提供します。  
  
 次のコードでは、ファイナライズ可能な型の例を示します。  
  
```  
public class ComplexResourceHolder : IDisposable {  
  
    private IntPtr buffer; // unmanaged memory buffer  
    private SafeHandle resource; // disposable handle to a resource  
  
    public ComplexResourceHolder(){  
        this.buffer = ... // allocates memory  
        this.resource = ... // allocates the resource  
    }  
  
    protected virtual void Dispose(bool disposing){  
            ReleaseBuffer(buffer); // release unmanaged memory  
        if (disposing){ // release other disposable objects  
            if (resource!= null) resource.Dispose();  
        }  
    }  
  
    ~ ComplexResourceHolder(){  
        Dispose(false);  
    }  
  
    public void Dispose(){  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
}  
```  
  
 **X 回避** ファイナライズ可能な型を作成します。  
  
 いかなる場合においてと思われる、ファイナライザーが必要なを慎重に検討します。 実際のパフォーマンスとコードの両方の複雑性の観点から、ファイナライザーを持つインスタンスに関連付けられているコストです。 などのリソースのラッパーを使用して必要に応じて <xref:System.Runtime.InteropServices.SafeHandle> を可能な場合は、アンマネージ リソースをカプセル化、その場合、ファイナライザーが不要になるラッパーが、独自のリソースのクリーンアップを行うためです。  
  
 **X のしないで** ファイナライズ可能な値の型を作成します。  
  
 実際には参照型のみが、CLR でファイナライズを取得し、したがってしようと値の型にファイナライザーを配置することは無視されます。 C\# および C\+\+ コンパイラは、この規則を適用します。  
  
 **✓ は** 型は独自のファイナライザーがない、アンマネージ リソースを解放する必要がある場合、型をファイナライズ可能なためです。  
  
 ファイナライザーを実装するときに呼び出します `Dispose(false)` 内のすべてのリソースのクリーンアップ ロジックを配置し、 `Dispose(bool disposing)` メソッドです。  
  
```  
public class ComplexResourceHolder : IDisposable {  
  
    ~ ComplexResourceHolder(){  
        Dispose(false);  
    }  
  
    protected virtual void Dispose(bool disposing){  
        ...  
    }  
}  
```  
  
 **✓ は** ファイナライズ可能なすべての種類の基本的な Dispose パターンを実装します。  
  
 これにより、型のユーザーはこのため、ファイナライザーにはそれらのリソースの確定的なクリーンアップを明示的に実行することを意味します。  
  
 **X のしないで** 、それらは既にファイナライズされている重大なリスクがあるため、ファイナライザーのコード パスでファイナライズ可能なオブジェクトにアクセスします。  
  
 たとえば、別のファイナライズ可能なオブジェクト B を参照しているファイナライズ可能なオブジェクト A に確実に使用できません B a のファイナライザー、またはその逆です。 \(クリティカル ファイナライズの弱い順序保証\) する場合を除きランダムな順序では、ファイナライザーが呼び出されます。  
  
 また、注意してを静的変数に格納されているオブジェクトが取得アプリケーション ドメインのアンロード中またはプロセスの終了中に、特定の時点でそれを収集します。 ファイナライズ可能なオブジェクト \(または静的変数に格納された値を使用する静的メソッドを呼び出す\) を参照する静的変数ができないにアクセスする場合は安全な <xref:System.Environment.HasShutdownStarted%2A?displayProperty=fullName> は true を返します。  
  
 **✓ は** ように、 `Finalize` 保護されているメソッド。  
  
 C\#、C\+\+、および VB.NET の開発者は、次のガイドラインを適用するコンパイラでは、役に立つため、これについて心配する必要はありません。  
  
 **X のしないで** システムに重大な障害を除く、ファイナライザーのロジックから let 例外エスケープします。  
  
 ファイナライザーは例外が、CLR がシャット ダウン \(.NET Framework version 2.0\)、現在のプロセス全体を実行して適切な方法で解放されているリソースを別のファイナライザーを妨げています。  
  
 **✓ を検討してください** を作成してクリティカル ファイナライズ可能なオブジェクトを使用して \(を含む型階層を持つ型 <xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>\) のファイナライザー絶対が実行される強制的なアプリケーション ドメインが発生しても状況をアンロードし、スレッドの中止します。  
  
 *部分 © 2005年、2009 Microsoft Corporation します。 All rights reserved.*  
  
 *翔泳社からのアクセス許可によって検出 [Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリを 2 nd Edition パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) は Cwalina Brad エイブラムスによる、Microsoft Windows の開発シリーズの一部として Addison\-wesley Professional、2008 年 10 月 22 日を公開します。*  
  
## 参照  
 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>   
 <xref:System.Object.Finalize%2A?displayProperty=fullName>   
 [Framework デザイン ガイドライン](../../../docs/standard/design-guidelines/index.md)   
 [一般的な設計パターン](../../../docs/standard/design-guidelines/common-design-patterns.md)   
 [Garbage Collection](../../../docs/standard/garbage-collection/index.md)