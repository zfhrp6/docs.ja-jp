---
title: ".NET Framework 4.6.1 におけるランタイムの変更点 | Microsoft ドキュメント"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- runtime changes, .NET Framework
- runtime changes, .NET Framework 4.6.1
- application compatibility
ms.assetid: 9d97421c-5fee-4523-98c9-a158e7e6a1ee
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: b8c6ec4d0bad4a769fb4d19a98c9e8a4eda0db78
ms.lasthandoff: 04/18/2017

---
# <a name="runtime-changes-in-the-net-framework-461"></a>.NET Framework 4.6.1 におけるランタイムの変更点
まれに、ランタイムの変更が、.NET Framework の以前のバージョンをターゲットとするものの、それ以降のバージョンの .NET Framework ランタイムで実行される既存のアプリに影響を与える可能性があります。 また、異なる .NET Framework ランタイム環境で実行されるアプリケーション間での動作に違いが生じます。 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] には、次の領域の変更が含まれています。  
  
-   [Windows Communication Foundation (WCF)](#WCF)  
  
-   [Windows Presentation Foundation (WPF)](#WPF)  
  
<a name="WCF"></a>   
## <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)  
  
|機能|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|`TransportWithMessageCredential` セキュリティ モードが指定された WCF バインド|既定では、`TransportWithMessageCredential` セキュリティ モードを使用する WCF バインドは、非対称セキュリティ キーの署名のない "to" ヘッダーを持つメッセージを許可しません。 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] で動作するアプリケーションから、この要件が緩和され、"to" ヘッダーに署名がないメッセージを受信できます。|これはオプトイン動作です。 署名のない "to" ヘッダーを持つメッセージを許可するには、次の構成設定をアプリケーションの構成ファイルの [\<<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに追加します。<br /><br /> `<runtime>     <AppContextSwitchOverrides value="Switch.System.ServiceModel.AllowUnsignedToHeader=true" />  </runtime>`<br /><br /> これはオプトイン機能であるため、既存のアプリの動作に影響はないはずです。|エッジ|  
  
<a name="WPF"></a>   
## <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
  
|機能|変更|影響|スコープ|  
|-------------|------------|------------|-----------|  
|<xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName>|<xref:System.Windows.Controls.ItemsControl> が仮想化 (<xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A> = `true`) および項目スクロール (<xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A>=<xref:System.Windows.Controls.ScrollUnit?displayProperty=fullName>) を使用してコレクションを表示し、コントロールがスクロールして、ピクセル単位の高さが近隣の他項目とは異なる項目が表示されると、<xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName> がコレクションに含まれるすべての項目をイテレーションします。   このイテレーション中に UI は応答しません。コレクションのサイズが大きい場合、ハングとして認識される場合があります。<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] より前のリリースであっても、このようなイテレーションは他の状況で発生します。 たとえば、異なる高さ (ピクセル単位) の項目が検出されたときにピクセル スクロール (<xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A>=<xref:System.Windows.Controls.ScrollUnit?displayProperty=fullName>) される場合や、近隣の項目よりも多い子孫項目を含む項目が検出されたときに階層データ (<xref:System.Windows.Controls.TreeView> コントロールまたはグループ化が有効になった <xref:System.Windows.Controls.ItemsControl>) が項目スクロールされる場合にイテレーションが発生します。<br /><br /> 項目スクロールと高さが異なる (ピクセル単位) 場合の対処方として、階層データのレイアウトのバグを修正できるようイテレーションが [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] で導入されました。  データがフラットである場合 (階層がない場合) は必要ないため、そのような状況であれば [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] は実行されません。|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] でイテレーションが発生し、以前のリリースでは発生しない場合、つまり <xref:System.Windows.Controls.ItemsControl> が異なる高さの (ピクセル単位) の項目を含むフラットなリストを項目スクロールしている場合、実行できる対応策は以下の 2 つです。<br /><br /> [.NET Framework Version 4.6.2](../../../docs/framework/install/guide-for-developers.md) をインストールします。<br /><br /> [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] に [修正プログラム HR 1605](https://support.microsoft.com/en-us/kb/3154529) をインストールします。|マイナー|  
## <a name="see-also"></a>関連項目  
 [4.6.1 のアプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)
