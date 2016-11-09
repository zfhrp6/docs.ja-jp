---
title: "アンマネージ リソースのクリーンアップ"
description: "アンマネージ リソースのクリーンアップ"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/18/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 8c97c3e2-8619-47ce-ae29-d6a3140bfa83
translationtype: Human Translation
ms.sourcegitcommit: 213ce098bcc2b5e31c55e759d895254d5ca33caa
ms.openlocfilehash: 692916bc5a9afd55dc4e3d0249386d2e3750895f

---

# <a name="cleaning-up-unmanaged-resources"></a>アンマネージ リソースのクリーンアップ

アプリケーションで作成するオブジェクトの大部分については、.NET のガベージ コレクターにメモリ管理を任せることができます。 しかし、アンマネージ リソースを含むオブジェクトを作成する場合は、アプリケーションでそのオブジェクトの使用が終了した時点で、そのリソースを明示的に解放する必要があります。 アンマネージ リソースの種類で最も一般的なのは、ファイル、ウィンドウ、ネットワーク接続、データベース接続などのオペレーティング システム リソースをラップしたオブジェクトです。 ガベージ コレクターは、アンマネージ リソースをカプセル化したオブジェクトを有効期間全体にわたって監視できますが、アンマネージ リソースを解放しクリーンアップする方法については情報を持っていません。 

型でアンマネージ リソースを使用している場合は、次のようにする必要があります。 

* Dispose パターンを実装します。 これは、アンマネージ リソースの確定的解放を有効にするために [IDisposable.Dispose](xref:System.IDisposable.Dispose) の実装を提供する必要があります。 型のコンシューマーはオブジェクト (および使用するリソース) が不要になると [Dispose](xref:System.IDisposable.Dispose) を呼び出します。 [Dispose](xref:System.IDisposable.Dispose) メソッドはアンマネージ リソースを直ちに解放します。 

* 型のコンシューマーが [Dispose](xref:System.IDisposable.Dispose) の呼び出しを忘れた場合にアンマネージ リソースを解放します。 これには、2 つの方法があります。 

    * アンマネージ リソースをラップするセーフ ハンドルを使用します。 この手法を使用することをお勧めします。 セーフ ハンドルは [System.Runtime.InteropServices.SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) クラスから派生し、堅牢な [Finalize](xref:System.Object.Finalize) メソッドを含みます。 セーフ ハンドルを使用するときは、単に [IDisposable](xref:System.IDisposable) インターフェイスを実装し、[IDisposable.Dispose](xref:System.IDisposable.Dispose) の実装でセーフ ハンドルの [Dispose](xref:System.IDisposable.Dispose) メソッドを呼び出します。 セーフ ハンドルのファイナライザーは、[Dispose](xref:System.IDisposable.Dispose) メソッドが呼び出されなかった場合、ガベージ コレクターによって自動的に呼び出されます。 

      または

    * [Object.Finalize](xref:System.Object.Finalize) メソッドをオーバーライドします。 終了処理では、型のコンシューマーが [IDisposable.Dispose](xref:System.IDisposable.Dispose) を呼び出してアンマネージ リソースを確定的に破棄しなかった場合に、リソースを非確定的に解放できます。 ただし、オブジェクトの終了処理は複雑でエラーが発生しやすい操作であるため、独自のファイナライザーを用意する代わりに、セーフ ハンドルを使用することをお勧めします。 

これで型のコンシューマーは、[IDisposable.Dispose](xref:System.IDisposable.Dispose) の実装を直接呼び出して、アンマネージ リソースで使用されるメモリを解放することができます。 [Dispose](xref:System.IDisposable.Dispose) メソッドを適切に実装すると、セーフ ハンドルの [Finalize](xref:System.Object.Finalize) メソッドまたは [Object.Finalize](xref:System.Object.Finalize) メソッドの独自のオーバーライドは、[Dispose](xref:System.IDisposable.Dispose) メソッドが呼び出されなかった場合にリソースをクリーンアップするための安全装置になります。 

## <a name="in-this-section"></a>このセクションの内容

[Dispose メソッドの実装](implementing-dispose.md) - アンマネージ リソースを解放する Dispose パターンを実装する方法について説明します。

[IDisposable を実装するオブジェクトの使用](using-objects.md) - 型のコンシューマーが Dispose の実装を確実に呼び出す方法について説明します。 このためには、C# の using ステートメントまたは Visual Basic の Using ステートメントを使用することをお勧めします。

## <a name="reference"></a>参照

[System.IDisposable](xref:System.IDisposable) - アンマネージ リソースの解放のための `Dispose` メソッドを定義します。

[Object.Finalize](xref:System.Object.Finalize) - アンマネージ リソースが `Dispose` メソッドによって解放されない場合に、オブジェクトの終了処理を提供します。 

[GC.SuppressFinalize](xref:System.GC#System_GC_SuppressFinalize_System_Object_) - 終了処理を抑制します。 このメソッドは、慣例的に `Dispose` メソッドから呼び出され、ファイナライザーが実行されないようにします。 



<!--HONumber=Nov16_HO1-->


