---
title: "発生したコレクション"
description: "発生したコレクション"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 3e09b9dd-a800-4e56-b468-619f910ae22e
translationtype: Human Translation
ms.sourcegitcommit: 213ce098bcc2b5e31c55e759d895254d5ca33caa
ms.openlocfilehash: 0bd8998cfb508294ffbc7a9619b571c9881ba294

---

# <a name="induced-collections"></a>発生したコレクション

ほとんどの場合、コレクションの実行に最適なタイミングはガベージ コレクターが判断できるので、ガベージ コレクターに任せるのが良い方法です。 ただし、ごくまれに、強制的にコレクションを実行するとアプリケーションのパフォーマンスが向上する場合があります。 このような場合は、[GC.Collect](xref:System.GC.Collect) メソッドを使用してガベージ コレクションを強制的に実行できます。 

アプリケーションのコードの特定の位置で、使用しているメモリ量が大きく減少する場合は、[Collect](xref:System.GC.Collect) メソッドを使用します。 たとえば、複数のコントロールのある複雑なダイアログ ボックスを使用するアプリケーションでは、ダイアログ ボックスを閉じるときに [Collect](xref:System.GC.Collect) を呼び出すと、ダイアログ ボックスの使用メモリが直ちに再利用されてパフォーマンスが向上する可能性があります。 適切でない回数でガベージ コレクターがオブジェクトの再利用を試みるとパフォーマンスが低下する場合があるので、アプリケーションではあまり頻繁にガベージ コレクションを強制しないでください。 次のセクションで説明するように、コレクションの効果がある場合にのみ、[Collect](xref:System.GC.Collect) メソッドに対して収集する [GCCollectionMode.Optimized](xref:System.GCCollectionMode.Optimized) の列挙値を指定できます。

## <a name="gc-collection-mode"></a>GC コレクション モード

[GCCollectionMode](xref:System.GCCollectionMode) 値を含む [GC.Collect](xref:System.GC.Collect) メソッド オーバーロードの 1 つを使用して、強制的コレクションの動作を次のように指定できます。

GCCollectionMode 値 | 説明
---------------------- | ----------- 
[既定値](xref:System.GCCollectionMode.Default) | 実行中のバージョンの .NET Framework の既定のガベージ コレクション設定を使用します。
[強制](xref:System.GCCollectionMode.Forced) | 直ちにガベージ コレクションを強制的に実行します。 これは、[GC.Collect()](xref:System.GC.Collect) オーバーロードを呼び出すことと同じです。 結果として、すべてのジェネレーションのフル ブロッキング コレクションになります。 また、直ちにフル ブロッキング ガベージ コレクションを強制的に実行する前に、[GCSettings.LargeObjectHeapCompactionMode](xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode) プロパティを [GCLargeObjectHeapCompactionMode.CompactOnce](xref:System.Runtime.GCLargeObjectHeapCompactionMode.CompactOnce) に設定して、大きなオブジェクト ヒープを圧縮することもできます。 
[最適化](xref:System.GCCollectionMode.Optimized) | オブジェクトを再利用するのに現在が最適なときかどうかをガベージ コレクターが判断できるようにします。 ガベージ コレクターは、コレクションの実行を正当化できるほど効果がないと判断して、オブジェクトを再利用せずに戻る場合があります。
 
## <a name="background-or-blocking-collections"></a>バックグラウンドまたはブロッキング コレクション

[GC.Collect(Int32, GCCollectionMode, Boolean)](xref:System.GC.Collect(System.Int32,System.GCCollectionMode,System.Boolean)) メソッド オーバーロードを呼び出して、発生するコレクションがブロッキング コレクションであるかどうかを指定できます。 実行されるコレクションの型は、メソッドの *mode* と *blocking* のパラメーターの組み合わせによって異なります。 *mode* は [GCCollectionMode](xref:System.GCCollectionMode) 列挙のメンバーで、*blocking* は [Boolean](xref:System.Boolean) 値です。 mode と blocking 引数の相互作用を次の表にまとめます。 

*モード* | *blocking* = true | *blocking* = false
------ | ----------------- | ------------------
[Forced](xref:System.GCCollectionMode.Forced) または [Default](xref:System.GCCollectionMode.Default) | ブロッキング コレクションはできるだけ早く実行されます。 バックグラウンド コレクションが実行中でジェネレーションが 0 または 1 の場合、[Collect(Int32, GCCollectionMode, Boolean)](xref:System.GC.Collect(System.Int32,System.GCCollectionMode,System.Boolean)) メソッドは直ちにブロッキング コレクションをトリガーし、コレクションが終了すると制御を戻します。 バックグラウンド コレクションが実行中で generation パラメーターが 2 の場合、メソッドはバックグラウンド コレクションの終了を待機し、ジェネレーション 2 のブロッキング コレクションをトリガーして、制御を戻します。 | コレクションはできるだけ早く実行されます。 [Collect(Int32, GCCollectionMode, Boolean)](xref:System.GC.Collect(System.Int32,System.GCCollectionMode,System.Boolean)) メソッドはバックグラウンド コレクションを要求しますが、それは保証されず、状況によってはブロッキング コレクションが実行される場合もあります。 バックグラウンド コレクションが既に実行中の場合、メソッドはすぐに制御を返します。 
[最適化](xref:System.GCCollectionMode.Optimized) | ガベージ コレクターおよび generation パラメーターの状態によっては、ブロッキング コレクションが実行される場合があります。 ガベージ コレクターは最適なパフォーマンスを提供しようとします。 | ガベージ コレクターの状態によっては、コレクションが実行される場合があります。 [Collect(Int32, GCCollectionMode, Boolean)](xref:System.GC.Collect(System.Int32,System.GCCollectionMode,System.Boolean)) メソッドはバックグラウンド コレクションを要求しますが、それは保証されず、状況によってはブロッキング コレクションが実行される場合もあります。 ガベージ コレクターは最適なパフォーマンスを提供しようとします。 バックグラウンド コレクションが既に実行中の場合、メソッドはすぐに制御を返します。 
 
## <a name="see-also"></a>関連項目

[待機モード](latency.md)

[.NET のガベージ コレクション](index.md)



<!--HONumber=Nov16_HO3-->


