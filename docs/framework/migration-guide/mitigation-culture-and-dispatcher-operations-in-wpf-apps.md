---
title: "軽減策: WPF アプリのカルチャおよびディスパッチャー操作"
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 41fc52679884d547809f1c1e9f47e29eb668cb8e
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-culture-and-dispatcher-operations-in-wpf-apps"></a>軽減策: WPF アプリのカルチャおよびディスパッチャー操作
.NET Framework 4.6 と .NET Framework 4.6.1 を対象とするアプリでは、<xref:System.Windows.Threading.Dispatcher> 内で <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> プロパティ、または <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> プロパティに対して加えられた変更は、ディスパッチャー操作の最後に失われます。 同様に、ディスパッチャー操作の外部で <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> または <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> に加えられた変更は、その操作の実行時には反映されない場合があります。  
  
 これは、<xref:System.Threading.ExecutionContext> が変更され、<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> と <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> が実行コンテキストに格納されるようになったためです。 WPF ディスパッチャー操作は、操作を開始するために使用された実行コンテキストを格納して、操作が完了したときに、以前のコンテキストを復元します。 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> と <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> がそのコンテキストの一部になったため、ディスパッチャー操作内でそれらに加えられた変更は、操作の外部では保持されません。  
  
## <a name="impact"></a>影響  
 具体的には、<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> プロパティと <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> プロパティに加えられた変更は、WPF UI コールバックと WPF アプリケーション内の他のコードとの間でフローされない場合があります。  
  
## <a name="mitigation"></a>軽減策  
 この変更の影響を受けるアプリは、次のいずれかの方法で回避できます。  
  
-   望ましい <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> または <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> をフィールドに格納し、正しい <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> または <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> が設定されているすべての <xref:System.Windows.Threading.Dispatcher> 操作の本体 (UI イベントのコールバック ハンドラーを含む) をチェックインする。  
  
-   <xref:System.Threading.ExecutionContext> の変更は、.NET Framework 4.6 または .NET Framework 4.6.1 を対象とする WPF アプリにのみ影響するため、対象を .NET Framework 4.5.2 とするか、4.6.2 以降のバージョンの .NET Framework を対象とすることで回避できます。  
  
## <a name="see-also"></a>関連項目  
 [変更の再ターゲット](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)

