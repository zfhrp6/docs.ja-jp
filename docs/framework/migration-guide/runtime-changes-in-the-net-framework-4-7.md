---
title: ".NET Framework 4.7 におけるランタイムの変更点 | Microsoft Docs"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- runtime changes,.NET Framework
- runtime changes,.NET Framework 4.7
- application compatibility
ms.assetid: 268eb334-7906-4e0b-a1e3-c74b745de2a5
caps.latest.revision: 8
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 321ec8f8293afad0f3da7fb6f907f45d404394cc
ms.contentlocale: ja-jp
ms.lasthandoff: 04/18/2017

---
# <a name="runtime-changes-in-the-net-framework-47"></a>.NET Framework 4.7 におけるランタイムの変更点

まれに、ランタイムの変更が、.NET Framework の以前のバージョンをターゲットとするものの、それ以降のバージョンの .NET Framework ランタイムで実行される既存のアプリに影響を与える可能性があります。 また、異なる .NET Framework ランタイム環境で実行されるアプリケーション間での動作に違いが生じます。 .NET Framework 4.6.2 には、次の領域の変更が含まれます。

- [Windows Presentation Foundation (WPF)](#WPF)

次の表の [スコープ] 列には、各変更の重要度を指定します。

- メジャー。 多数のアプリに影響するか、またはコードに大幅な変更が必要な、重大な変更。 変更の再ターゲットはこのカテゴリに分類されないことに注意してください。

- マイナー。 少数のアプリに影響するか、またはコードにわずかな変更が必要な、変更。

- エッジ。 一般的ではない特定のシナリオでアプリに影響を与える変更。

- 透過。 アプリの開発者やユーザーには大きな影響を及ぼさない変更。 アプリはこの変更のために変更を加える必要はありません。

## <a name="a-namewpf--windows-presentation-foundation-wpf"></a><a name="WPF" /> Windows Presentation Foundation (WPF)

assetId:///M:System.Windows.Controls.DataGridCellsPanel.BringIndexIntoView(System.Int32)?qualifyHint=False&autoUpgrade=True

| 特性 | 変更 | 影響 | スコープ |
|---|---|---|---|
| <xref:System.Windows.Controls.DataGridCellsPanel.BringIndexIntoView%2A> メソッド | .NET Framework 4.6.2 では、列の仮想化が有効になっているが列の幅が決定されていない場合、<xref:System.Windows.Controls.DataGridCellsPanel.BringIndexIntoView%2A> メソッドが非同期で実行されます。 非同期操作が完了する前に列が削除されると、<xref:System.ArgumentOutOfRangeException> が発生する場合があります。<br/></br>.NET Framework 4.7 以降、このシナリオでは例外がスローされなくなりました。 | この変更により、メソッドの信頼性が向上します。 | エッジ | 
|<xref:System.Windows.Controls.Ribbon.RibbonGroup> バックグラウンド | .NET Framework 4.6.2 とそれ以前のバージョンでは、ローカライズされたビルドの <xref:System.Windows.Controls.Ribbon.RibbonGroup> の背景が透明のブラシで塗りつぶされており、結果的に UI の操作性が低下していました。 .NET Framework 4.7 では、WPF で <xref:System.Windows.Controls.Ribbon.RibbonGroup> コントロールのローカライズされたリソースが更新されているため、正しいブラシが選択されます。 | 新しい動作を利用するには、.NET Framework 4.7 にアップグレードしてください。 | エッジ |
| WPF スペル チェック | .NET Framework 4.6.1 以降、WPF アプリケーションのシャットダウン中に、スペル チェックによって <xref:System.ObjectDisposedException> がスローされることがありました。 <br/><br/>.NET Framework 4.7 では、例外がランタイムによって正常に処理されるため、アプリケーションが悪影響を受けることがなくなります。 ただし、デバッグ時に実行中のアプリケーションで初回例外が見られる場合があるので注意してください。  | 新しい動作を利用するには、.NET Framework 4.7 にアップグレードしてください。   | エッジ |

## <a name="see-also"></a>関連項目

[.NET Framework 4.7 のアプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-7.md)


