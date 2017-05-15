---
title: "軽減策: 水平方向スクロールおよび仮想化 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d5bafd9b-a3b3-4f92-8241-2aad254fb1a9
caps.latest.revision: 6
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 37c60fd8a3e3e4e44dc00e278f6edafcdd766c03
ms.contentlocale: ja-jp
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-horizontal-scrolling-and-virtualization"></a>軽減策: 水平方向スクロールおよび仮想化
この変更は、メインのスクロール方向と直交する方向で独自に仮想化を行う <xref:System.Windows.Controls.ItemsControl> に適用されます  (主な例として、<xref:System.Windows.Controls.DataGrid.EnableColumnVirtualization%2A> が `true` に設定されている <xref:System.Windows.Controls.DataGrid> コントロールがあります)。特定の水平方向スクロール操作の結果が変更され、比較可能な垂直操作の結果により類似した、より直感的な結果が生成されるようになりました。  特定の操作には**ここにスクロール**や**右端**などがあり、水平スクロール バーを右クリックすると表示されるメニューから名前を使用することができます。  これらの両方でオフセット候補が計算され、<xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset%2A?displayProperty=fullName> が呼び出されます。  新しいオフセットにスクロールすると、"ここ" または "右端" の定義が変更されている場合があります。これは、新しく非仮想化されたコンテンツで <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A?displayProperty=fullName> の値が変更されたためです。  
  
## <a name="description-of-the-change"></a>変更の説明  
 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] より前では、もう "ここ" や "右端" にない場合でも、スクロール操作では単にオフセット候補を使用します。  その結果、スクロールつまみの "バウンス" などの効果が得られます。たとえば、  <xref:System.Windows.Controls.DataGrid> コントロールで <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A> が 1000 に設定され、<xref:System.Windows.FrameworkElement.Width%2A> が 200 に設定されているとします。  "右端" へのスクロールでは、1000 - 200 = 800 というオフセット候補を使用します。  そのオフセットへのスクロール時に、新しい列が非仮想化されます。これらの列が非常に広いため、<xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A> を 2000 に変更したとします。  スクロールは <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset%2A>=800 で終了し、つまみはスクロールバーの中央付近 (正確には 800/2000 = 40%) に "戻り" ます。  
  
 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 以降では、このような場合に新しいオフセット候補が再計算されます  (垂直方向スクロールの動作は既にこのようになっています)。  
  
## <a name="impact"></a>影響  
 この変更により、エンド ユーザーにはより予測可能で直感的なエクスペリエンスが提供されるようになりますが、水平方向スクロール後の <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset%2A?displayProperty=fullName> の正確な値に依存するアプリに影響する可能性もあります。これは、<xref:System.Windows.Controls.Primitives.IScrollInfo.SetHorizontalOffset%2A?displayProperty=fullName> の明示的な呼び出しによるものであるか、エンド ユーザーによる呼び出しであるかに関係ありません。  
  
## <a name="mitigation"></a>軽減策  
 <xref:System.Windows.Controls.Primitives.IScrollInfo.HorizontalOffset%2A?displayProperty=fullName> の予測値を使用するアプリを、非仮想化により <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A> が変更される可能性のある水平方向スクロール後の実際の値 (および <xref:System.Windows.Controls.Primitives.IScrollInfo.ExtentWidth%2A> の値) を取得するように変更する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [ランタイムの変更点](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6-2.md)
