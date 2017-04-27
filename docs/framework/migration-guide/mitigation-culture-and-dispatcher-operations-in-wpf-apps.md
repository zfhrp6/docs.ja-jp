---
title: "軽減策: WPF アプリのカルチャおよびディスパッチャー操作 | Microsoft Docs"
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
ms.assetid: 455c1452-8ce0-45ae-a092-21fb8edf1cac
caps.latest.revision: 3
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 1aee32c5c50c4ff4309f93bff270e6c3b3c8f7cc
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-culture-and-dispatcher-operations-in-wpf-apps"></a>軽減策: WPF アプリのカルチャおよびディスパッチャー操作
.NET Framework 4.6 および .NET Framework 4.6.1 を対象とするアプリの場合、<xref:System.Windows.Threading.Dispatcher> 内で <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> プロパティまたは <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> プロパティに対して加えられたた変更は、ディスパッチャー操作の最後に失われます。 同様に、ディスパッチャー操作外で <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> または <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> に加えられた変更は、操作実行時に反映されない場合があります。  
  
 <xref:System.Threading.ExecutionContext> が変更され、<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> と <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> が実行コンテキストに格納されるようになったためです。 WPF ディスパッチャー操作は、操作を開始するために使用された実行コンテキストを格納して、操作が完了したときに、以前のコンテキストを復元します。 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> と <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> は実行コンテキストに格納されるようになったため、ディスパッチャー操作内の変更は操作外で保持されません。  
  
## <a name="impact"></a>影響  
 これは事実上、<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> プロパティおよび <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> プロパティに加えられた変更は、WPF の UI のコールバックと WPF アプリケーションのその他のコードの間でフローしないことを意味します。  
  
## <a name="mitigation"></a>軽減策  
 この変更の影響を受けるアプリは、次のいずれかの方法で回避できます。  
  
-   フィールドに <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> または <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> を格納し、正しい <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> または <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> が設定されているすべての <xref:System.Windows.Threading.Dispatcher> 操作の本文 (UI イベントのコールバック ハンドラーを含む) をチェックインする。  
  
-   <xref:System.Threading.ExecutionContext> の変更は、.NET Framework 4.6 または .NET Framework 4.6.1 をターゲットとする WPF アプリにのみ影響するため、ターゲットを .NET Framework 4.5.2 とするか、4.6.2 以降のバージョンの .NET Framework をターゲットとすることで回避できます。  
  
## <a name="see-also"></a>関連項目  
 [変更の再ターゲット](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
