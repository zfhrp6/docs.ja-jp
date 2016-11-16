---
title: "待機モード"
description: "待機モード"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 08/18/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 810bd8be-5a48-42c6-b080-3afdb31fc61b
translationtype: Human Translation
ms.sourcegitcommit: de0dab146fc811e895dc32f98f877db5e757f82b
ms.openlocfilehash: e063482aaa1fad01f8e0cd9e8552c87a0b247571

---

# <a name="latency-modes"></a>待機モード

オブジェクトを再利用するには、ガベージ コレクターはアプリケーションで実行中のすべてのスレッドを停止する必要があります。 状況によっては、アプリケーションがデータの取得やコンテンツの表示を行うときなど、重要なときにフル ガベージ コレクションが発生し、パフォーマンスが低下することがあります。 ガベージ コレクターが作業に悪影響を与える度合いを調整するには、[GCSettings.LatencyMode](xref:System.Runtime.GCSettings.LatencyMode) プロパティを [System.Runtime.GCLatencyMode](xref:System.Runtime.GCLatencyMode) 値のいずれかに設定します。 

Latency (待機時間) は、ガベージ コレクターが実行中のアプリケーションに割って入る時間を指します。 待機時間が短い場合、ガベージ コレクターがオブジェクトを再利用する処理は控えめになり、アプリケーションに悪影響を与える度合いが下がります。 [System.Runtime.GCLatencyMode](xref:System.Runtime.GCLatencyMode) 列挙により、2 つの短い待機時間設定を指定できます。

* [LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency) では、ジェネレーション 2 のガベージ コレクションが停止し、ジェネレーション 0 および 1 のみガベージ コレクションが実行されます。 これは、短時間の場合にのみ使用できます。 この設定を長時間にわたって使用すると、システムのメモリが不足してガベージ コレクターがガベージ コレクションをトリガーした場合に、アプリケーションが少しの間停止したり、高速性を必要とする操作が中断されたりすることがあります。 この設定は、ワークステーションのガベージ コレクションでのみ使用できます。 

* [SustainedLowLatency](xref:System.Runtime.GCLatencyMode.SustainedLowLatency) では、フォアグラウンドのジェネレーション 2 のガベージ コレクションが停止し、ジェネレーション 0 および 1 とバックグラウンドのジェネレーション 2 のガベージ コレクションのみが実行されます。 これは長時間にわたって使用でき、ワークステーションとサーバーの両方のガベージ コレクションで使用できます。 この設定は、[同時実行ガベージ コレクション](https://msdn.microsoft.com/library/yhwwzef8.aspx)が無効の場合には使用できません。

待機時間の短い設定になっている場合でも、次の状況ではジェネレーション 2 のガベージ コレクションの停止が解除されます。

* システムがオペレーティング システムからメモリ不足の通知を受け取った場合。

* アプリケーション コードから [GC.Collect](xref:System.GC.Collect(System.Int32)) メソッドを呼び出し、generation パラメーターに 2 を指定してガベージ コレクションを実行した場合。

次の表に、[GCLatencyMode](xref:System.Runtime.GCLatencyMode) の各値を使用するアプリケーション シナリオを示します。

待機時間モード | アプリケーション シナリオ
------------ | --------------------- 
[Batch](xref:System.Runtime.GCLatencyMode.Batch) | UI 操作のないアプリケーションの場合、またはサーバー側の操作の場合に使用します。 これは、[同時実行ガベージ コレクション](https://msdn.microsoft.com/library/yhwwzef8.aspx)が無効の場合の既定モードです。
[Interactive](xref:System.Runtime.GCLatencyMode.Interactive) | UI を持つほとんどのアプリケーションの場合に使用します。 UI 操作のないアプリケーションの場合、またはサーバー側の操作の場合に使用します。 これは、[同時実行ガベージ コレクション](https://msdn.microsoft.com/library/yhwwzef8.aspx)が有効の場合の既定モードです。
[LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency) | ガベージ コレクターからの割り込みにより重大な影響を受け、高速性を必要とする、短期間の操作を実行するアプリケーションの場合に使用します。 たとえば、アニメーションのレンダリングやデータの取得機能を実行するアプリケーションなどがあります。
[SustainedLowLatency](xref:System.Runtime.GCLatencyMode.SustainedLowLatency) | ガベージ コレクターからの割り込みにより重大な影響を受け、高速性を必要とする、さほど処理時間を必要としないものの長時間になる可能性のある操作を実行するアプリケーションの場合に使用します。 たとえば、取引時間中に市場データの変化に応じて迅速な応答時間を必要とするアプリケーションなどがあります。   このモードでは、マネージ ヒープのサイズが他のモードより大きくなります。 マネージ ヒープは最適化されないため、断片化の割合が高くなる可能性があります。 十分なメモリが使用可能であることを確認してください。
 
## <a name="guidelines-for-using-low-latency"></a>待機時間の短いモードの使用に関するガイドライン

[LowLatency](xref:System.Runtime.GCLatencyMode.LowLatency) モードを使用する場合は、次のガイドラインを検討してください。

* 待機時間を短くする期間は、できるだけ短くします。

* 待機時間を短くする期間中は、大量のメモリを割り当てないようにします。 ガベージ コレクションによって再利用されるオブジェクトの数が少なくなるため、メモリ不足の通知が発生する可能性があります。 

* 待機時間の短いモードの間は、割り当ての数、特に大きなオブジェクト ヒープや固定されたオブジェクトへの割り当ての数を最小限に抑えます。 

* 割り当てられる可能性のあるスレッドに注意します。 [LatencyMode](xref:System.Runtime.GCSettings.LatencyMode) プロパティの設定はプロセス全体に適用されるため、割り当てられた他のスレッドで [OutOfMemoryException](xref:System.OutOfMemoryException) が発生する可能性があります。 

* 待機時間を短くする期間中でも、[GC.Collect(Int32, GCCollectionMode)](xref:System.GC.Collect(System.Int32,System.GCCollectionMode)) メソッドを呼び出せばジェネレーション 2 のガベージ コレクションを強制できます。

## <a name="see-also"></a>関連項目

[System.GC](xref:System.GC)

[発生したコレクション](induced.md)

[.NET のガベージ コレクション](index.md)



<!--HONumber=Nov16_HO1-->


