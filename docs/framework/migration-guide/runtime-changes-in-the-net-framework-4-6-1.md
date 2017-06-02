---
title: ".NET Framework 4.6.1 におけるランタイムの変更点 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET Framework のランタイム変更"
  - ".NET Framework 4.6.1 のランタイム変更"
  - "アプリケーションの互換性"
ms.assetid: 9d97421c-5fee-4523-98c9-a158e7e6a1ee
caps.latest.revision: 5
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 5
---
# .NET Framework 4.6.1 におけるランタイムの変更点
まれに、ランタイムの変更が、.NET Framework の以前のバージョンをターゲットとするものの、それ以降のバージョンの .NET Framework ランタイムで実行される既存のアプリに影響を与える可能性があります。 また、異なる .NET Framework ランタイム環境で実行されるアプリケーション間での動作に違いが生じます。 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]次の領域の変更が含まれています。  
  
-   [Windows Communication Foundation (WCF)](#WCF)  
  
-   [Windows Presentation Foundation (WPF)](#WPF)  
  
<a name="WCF"></a>   
## <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)  
  
|機能|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|WCF バインド、`TransportWithMessageCredential`セキュリティ モード|既定では、WCF のバインディングを使用して、`TransportWithMessageCredential`セキュリティ モードは、符号なしでメッセージを許可しない"to"非対称セキュリティ キーのヘッダー。 以降で実行されるアプリで、[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]には署名しません"to"ヘッダー メッセージの送受信をこの要件が緩和することはできます。|これはオプトイン動作です。 符号なしの"to"ヘッダーを持つメッセージを許可する、次の構成設定を追加する、 [ <> \> ](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)アプリの構成ファイルのセクション。<br /><br /> `<runtime>     <AppContextSwitchOverrides value="Switch.System.ServiceModel.AllowUnsignedToHeader=true" />  </runtime>`<br /><br /> これはオプトイン機能であるため、既存のアプリの動作に影響はないはずです。|エッジ|  
  
<a name="WPF"></a>   
## <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
  
|機能|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|<xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName>|ときに、 <xref:System.Windows.Controls.ItemsControl>仮想化を使用して、コレクションが表示されます (<xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A> = `true`) と項目スクロール (<xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A>=<xref:System.Windows.Controls.ScrollUnit?displayProperty=fullName>)、コントロールのスクロールの高さ (ピクセル単位) は、その近隣ノードによって異なります。 項目を表示するときと、 <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName>コレクション内のすべての項目を反復処理します。   この反復処理中には、UI が応答しません。 コレクションのサイズが大きい場合、ハングとこれに認識されることができます。<br /><br /> 前のリリースであっても、他の状況で発生したこのイテレーション、[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]です。 ピクセル スクロールする場合に発生するなど (<xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A>=<xref:System.Windows.Controls.ScrollUnit?displayProperty=fullName>) 項目スクロールする場合に、別のピクセルの高さ、および項目を検出したときに階層データ (ようにこのような<xref:System.Windows.Controls.TreeView>コントロールまたは<xref:System.Windows.Controls.ItemsControl>とグループ化を有効になっている) 近隣ノードよりも下位の項目の数が異なる項目に遭遇するとします。<br /><br /> 項目のスクロールと別のピクセルの高さの場合、イテレーションがで導入された、[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]階層データのレイアウトでバグを修正します。  データがフラットである場合は必要ありません (持ちません階層)、および[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]されないという点です。|イテレーションが発生した場合、 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] --つまりの以前のリリースではなく場合、 <xref:System.Windows.Controls.ItemsControl>は項目のスクロール単純なリストに別のピクセルの高さ--の項目は、2 つの対応策。<br /><br /> インストール、 [.NET Framework 4.6.2](../../../docs/framework/install/guide-for-developers.md)します。<br /><br /> インストール[修正プログラム HR 1605](https://support.microsoft.com/en-us/kb/3154529)の[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]です。|マイナー|  
  
## <a name="see-also"></a>関連項目  
 [4.6.1 アプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)