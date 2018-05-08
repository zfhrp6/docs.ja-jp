---
title: Dispose パターン
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Dispose method
- class library design guidelines [.NET Framework], Dispose method
- class library design guidelines [.NET Framework], Finalize method
- customizing Dispose method name
- Finalize method
ms.assetid: 31a6c13b-d6a2-492b-9a9f-e5238c983bcb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bdcb746ae2d8c2262b0cd0c6c9dcaababb12bd63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="dispose-pattern"></a>Dispose パターン
すべてのプログラムは、それらの実行の進行中にメモリ、システムのハンドル、またはデータベース接続など、1 つまたは複数のシステム リソースを取得します。 開発者は、取得し、使用後に解放する必要があるためには、このようなシステム リソースを使用する場合は注意が必要があります。  
  
 CLR は、自動メモリ管理のサポートを提供します。 マネージ メモリ (c# 演算子を使用して割り当てられたメモリ`new`) 明示的に解放する必要はありません。 ガベージ コレクター (GC) によって自動的に解放されます。 これにより、開発者は、メモリを解放する難しい面倒な作業を解放し、.NET Framework によって提供される画期的な生産性向上のための主な理由の 1 つです。  
  
 残念ながら、マネージ メモリは、さまざまな種類のシステム リソースの 1 つです。 ただし、マネージ メモリ以外のリソースは明示的に解放する必要あるし、アンマネージ リソースと呼びます。 GC が具体的には想定していません、このようなアンマネージ リソースを管理するには、開発者の手にアンマネージ リソースを管理する責任があることを意味します。  
  
 CLR では、アンマネージ リソースを解放するときにいくつかのヘルプを提供します。 <xref:System.Object?displayProperty=nameWithType> 仮想メソッドを宣言<xref:System.Object.Finalize%2A>(ファイナライザーとも呼ばれます) 前に、オブジェクトのメモリ GC によって解放され、アンマネージ リソースを解放するをオーバーライドすることができます、GC によって呼び出されます。 ファイナライザーをオーバーライドする型は、ファイナライズ可能な型と呼ばれます。  
  
 ファイナライザーは、一部のクリーンアップのシナリオで効果的なは、2 つの重要な欠点があります。  
  
-   ファイナライザーは、GC では、オブジェクトがコレクションの対象となることが検出された場合に呼び出されます。 これは、不定一定時間、リソースが今後不要後に行われます。 開発者がでしたまたはリソースとリソースが実際には、ファイナライザーで解放ときの時刻をリリースする場合の間の遅延が多く不足しているリソース (が簡単に不足したりリソース) を取得するプログラムでもは許容できない可能性があります。リソースの使用 (大規模なアンマネージ メモリ バッファーなど) に保持するコストのかかるがである場合。  
  
-   CLR は、ファイナライザーを呼び出す必要がある、ときに、次は、ガベージ コレクション (コレクション間で実行するファイナライザー) のラウンドするまで、オブジェクトのメモリのコレクションを延期にする必要があります。 これは、オブジェクトのメモリ (およびを参照してすべてのオブジェクト) は時間の長い期間に解放されないことを意味します。  
  
 そのため、ファイナライザーでのみ証明書利用者できない可能性があります、不足しているリソースを処理する場合、可能な限り早くアンマネージ リソースを解放する必要がある場合、多くのシナリオで、または高パフォーマンスの高いシナリオで適切な GC の追加のオーバーヘッドファイナライズは許容されません。  
  
 フレームワークは、提供、<xref:System.IDisposable?displayProperty=nameWithType>インターフェイスを手動で必要でないとすぐに、アンマネージ リソースを解放することを開発者に提供するために実装する必要があります。 用意されています、<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>するように、GC が知ることができるメソッド オブジェクトの破棄が手動で必要としない、完了するをその場合、オブジェクトのメモリを再要求できる前です。 実装する型、`IDisposable`インターフェイスが破棄可能な型と呼びます。  
  
 Dispose パターンは、使用状況およびファイナライザーの実装を標準化するためのものと`IDisposable`インターフェイスです。  
  
 パターンの主要な動機がの実装の複雑さを軽減するには、<xref:System.Object.Finalize%2A>と<xref:System.IDisposable.Dispose%2A>メソッドです。 複雑さのメソッドがいくつかのコード パスが (相違点は後で説明) を共有することに由来します。 さらに、履歴上の理由から決定論的リソース管理のための言語サポートの進化に関連するパターンの一部の要素があります。  
  
 **✓ しないで**破棄可能な型のインスタンスを含む型で、基本的な Dispose パターンを実装します。 参照してください、 [Dispose の基本的なパターン](#basic_pattern)基本的なパターンの詳細セクションです。  
  
 型が破棄可能なその他のオブジェクトの有効期間を担当する場合は、開発者はすぎる、それらを破棄する方法を必要があります。 使用して、コンテナーの`Dispose`実現する便利な方法です。  
  
 **✓ しないで**基本の Dispose パターンを実装し、保持しているリソースを明示的に解放できる必要があると、ファイナライザーがない型でファイナライザーを用意します。  
  
 たとえば、アンマネージ メモリ バッファーを格納する型で、パターンを実装する必要があります。 [ファイナライズ可能な型](#finalizable_types)ファイナライザーを実装する関連のガイドラインについて説明します。  
  
 **✓ を検討してください**基本の Dispose パターンを実装するクラスでのリソースとアンマネージ自体を保持しないことや、破棄可能なオブジェクトは、実行のサブタイプをされている可能性がします。  
  
 これの好例が、<xref:System.IO.Stream?displayProperty=nameWithType>クラスです。 抽象基本クラスのすべてのリソースを保持しませんが、そのサブクラスのほとんどは、このため、このパターンを実装します。  
  
<a name="basic_pattern"></a>   
## <a name="basic-dispose-pattern"></a>基本の Dispose パターン  
 基本的なパターンの実装では、実装では、`System.IDisposable`インターフェイスを宣言する、`Dispose(bool)`間で共有するすべてのリソースのクリーンアップ ロジックを実装するメソッド、`Dispose`メソッドと省略可能な終了します。  
  
 次の例は、基本的なパターンの簡単な実装を示しています。  
  
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
  
 ブール型パラメーター`disposing`から呼び出されたメソッドであるかどうかを示す、`IDisposable.Dispose`実装またはファイナライザーからです。 `Dispose(bool)`実装は、その他の参照オブジェクト (上記のサンプルのリソース フィールドなど) にアクセスする前に、パラメーターを確認する必要があります。 このようなオブジェクトからこのメソッドが呼び出された場合にのみアクセスする必要があります、`IDisposable.Dispose`実装 (ときに、`disposing`パラメーターが true に等しい)。 メソッドがファイナライザーから呼び出された場合 (`disposing`は false)、その他のオブジェクトにアクセスしないようにします。 オブジェクトが予期しない順序で完了し、ため、またはその依存関係のいずれかが既にが完了することです。  
  
 また、このセクションでは、Dispose パターンが実装していません基数を持つクラスに適用されます。 オーバーライドするだけで既にパターンを実装するクラスから継承している場合、`Dispose(bool)`追加のリソースのクリーンアップ ロジックを提供します。  
  
 **✓ しないで**宣言、`protected virtual void Dispose(bool disposing)`アンマネージ リソースの解放に関連するすべてのロジックを集中管理するメソッド。  
  
 すべてのリソースのクリーンアップは、このメソッドで発生する必要があります。 両方のファイナライザーからメソッドを呼び出したと`IDisposable.Dispose`メソッドです。 パラメーターは、ファイナライザーの内部から呼び出されている場合は false になります。 終了処理中に実行されるコードがファイナライズ可能なその他のオブジェクトにアクセスしていないことを確認することを使用してください。 ファイナライザーの実装の詳細については、次のセクションで説明します。  
  
```  
protected virtual void Dispose(bool disposing){  
    if (disposing){  
        if (resource!= null) resource.Dispose();  
    }  
}  
```  
  
 **✓ しないで**実装、`IDisposable`だけ呼び出すことによってインターフェイス`Dispose(true)`続く`GC.SuppressFinalize(this)`です。  
  
 呼び出し`SuppressFinalize`場合にのみ発生`Dispose(true)`が正常に実行します。  
  
```  
public void Dispose(){  
    Dispose(true);  
    GC.SuppressFinalize(this);  
}  
```  
  
 **X しないで**パラメーターなしで行う`Dispose`仮想メソッドです。  
  
 `Dispose(bool)`メソッドであるサブクラスによってオーバーライドする必要があります。  
  
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
  
 **X しないで**のすべてのオーバー ロードを宣言、`Dispose`以外のメソッド`Dispose()`と`Dispose(bool)`です。  
  
 `Dispose` このパターンを体系化し、実装、ユーザー、およびコンパイラの間での混乱を回避するために予約語を考慮ください。 一部の言語は、特定の種類に自動的にこのパターンを実装することもできます。  
  
 **✓ しないで**を許可する、`Dispose(bool)`に複数回呼び出されるメソッド。 メソッドは、最初の呼び出し後に何もすることもできます。  
  
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
  
 **避け x**内から例外をスローして`Dispose(bool)`されている重要な状況で格納しているプロセスが破損している場合を除き (リークを一貫性のない共有状態などです。)。  
  
 ユーザーが期待するへの呼び出し`Dispose`例外は発生しません。  
  
 場合`Dispose`例外を発生させる可能性があります、これ以上の finally ブロックのクリーンアップ ロジックは実行されません。 この問題を回避する、ユーザーが すべての呼び出しをラップする必要があります`Dispose`(内で、finally ブロック!)、try ブロックで非常に複雑なクリーンアップ ハンドラーにつながります。 実行している場合、`Dispose(bool disposing)`メソッド、破棄が false の場合に例外がスローされません。 これによりファイナライザー コンテキスト内で実行されている場合、プロセスが終了されます。  
  
 **✓ しないで**スロー、<xref:System.ObjectDisposedException>オブジェクトが破棄された後は使用できませんのすべてのメンバーからです。  
  
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
  
 **✓ を検討してください**メソッドを提供する`Close()`に加え、`Dispose()`領域での一般的な用語が閉じるかどうかは。  
  
 これを行うことが重要を作成すること、`Close`実装と同じ`Dispose`を実装することを検討してください、`IDisposable.Dispose`メソッドに明示的にします。  
  
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
## <a name="finalizable-types"></a>ファイナライズ可能な型  
 ファイナライズ可能な型はファイナライザーをオーバーライドして、終了コードのパスを提供することによって、基本的な Dispose パターンを拡張する型は、`Dispose(bool)`メソッドです。  
  
 ファイナライザーは、実行中に、システムの状態に関する (通常は有効な) 仮定をすることはできませんので、主に正しく実装する非常に困難です。 慎重に検討には、次のガイドラインを考慮する必要があります。  
  
 ガイドラインの一部がしないようにだけに適用されるに注意してください、`Finalize`メソッド、ファイナライザーからすべてのコードが呼び出されます。 つまり、ロジック内で実行される場合は、基本的な Dispose パターン以前に定義した、`Dispose(bool disposing)`ときに、`disposing`パラメーターを false にします。  
  
 基本クラス既にファイナライズ可能な基本的な Dispose パターンを実装場合、する必要がありますはオーバーライド`Finalize`もう一度です。 代わりにだけをオーバーライドする、`Dispose(bool)`追加のリソースのクリーンアップ ロジックを提供します。  
  
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
  
 **避け x**ファイナライズ可能な型を作成します。  
  
 いかなる場合においてもいると思われるファイナライザーが必要な慎重に検討します。 実際のパフォーマンスとコードの両方の複雑さの観点からのファイナライザーを持つインスタンスに関連付けられているコスト。 などのリソースのラッパーを使用して必要に応じて<xref:System.Runtime.InteropServices.SafeHandle>を可能な場合は、アンマネージ リソースをカプセル化する、その場合、ファイナライザーが不要になるラッパーが独自のリソースのクリーンアップを行うためです。  
  
 **X しないで**ファイナライズ可能な値の型を作成します。  
  
 実際には参照型のみが、CLR によって終了取得され、値の型でファイナライザーを配置するあらゆる試みは無視されるためです。 C# および C++ コンパイラは、この規則を強制します。  
  
 **✓ しないで**型は独自のファイナライザーがない、アンマネージ リソースを解放する必要がある場合の種類をファイナライズようにします。  
  
 ファイナライザーを実装する場合を呼び出すだけ`Dispose(false)`内のすべてのリソースのクリーンアップ ロジックを配置し、`Dispose(bool disposing)`メソッドです。  
  
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
  
 **✓ しないで**ファイナライズ可能な型で、基本的な Dispose パターンを実装します。  
  
 これにより、型のユーザーは明示的にファイナライザーが担当する同じリソースの確定的なクリーンアップを実行することを意味します。  
  
 **X しないで**こと、が既に終了されている重大なリスクがあるため、ファイナライザーのコード パスに、ファイナライズ可能なオブジェクトにアクセスします。  
  
 たとえば、別のファイナライズ可能なオブジェクト B を参照しているファイナライズ可能なオブジェクト A 確実にでは使用できません B A のファイナライザー、またはその逆です。 ファイナライザーは、(重要な終了処理の弱い順序保証) する場合を除きランダムな順序で呼び出されます。  
  
 また、アプリケーション ドメインのアンロード中またはプロセスの終了中に、静的変数に格納されているオブジェクトは特定の時点で収集取得こともあります。 ファイナライズ可能なオブジェクト (または静的変数に格納された値を使用する静的メソッドを呼び出す) を参照する静的変数ができない可能性がありますにアクセスする場合は安全な<xref:System.Environment.HasShutdownStarted%2A?displayProperty=nameWithType>は true を返します。  
  
 **✓ しないで**ように、`Finalize`保護されているメソッド。  
  
 C#、C++、および VB.NET の開発者は、このガイドラインを適用すると、コンパイラに役立つため、これについて心配する必要はありません。  
  
 **X しないで**システムに重大な障害を除く、ファイナライザーのロジックから使用すると、例外のエスケープします。  
  
 ファイナライザーから例外をスローすると場合、CLR はシャット ダウンの時点で .NET Framework version 2.0)、プロセス全体を実行して適切な方法で解放されてからのリソースから他のファイナライザーを防止します。  
  
 **✓ を検討してください**を作成して、重要なファイナライズ可能なオブジェクトを使用して (を含む型階層を持つ型<xref:System.Runtime.ConstrainedExecution.CriticalFinalizerObject>) の状況でファイナライザーどうしても必要があります実行発生した場合でも強制アプリケーション ドメインのアンロード スレッド中止します。  
  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>  
 <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)  
 [共通デザイン パターン](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 [ガベージ コレクション](../../../docs/standard/garbage-collection/index.md)
