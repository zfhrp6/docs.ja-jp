---
title: "軽減策: カルチャおよび非同期操作 | Microsoft Docs"
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
ms.assetid: d2cdb578-9923-47df-9ffd-5865333ac1a4
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c2dbf60cacf47be3c448b5683b771840ef85ddaf
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-culture-and-asynchronous-operations"></a>軽減策: カルチャおよび非同期操作
[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 以降のバージョンを対象とするアプリの場合、<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> と <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> がスレッドの <xref:System.Threading.ExecutionContext> に格納され、これは非同期操作全体にフローします。  
  
## <a name="impact"></a>影響  
 この変更の結果、<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> または <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> が変更されると、後で非同期に実行されるタスクに反映されるようになります。 これは、旧バージョンの .NET Framework の動作とは異なります。旧バージョンのすべての非同期タスクでは、<xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> と <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> はシステムの既定値にリセットされます。  
  
## <a name="mitigation"></a>軽減策  
 この変更の影響を受けるアプリは、次のいずれかの方法で回避できます。  
  
-   非同期タスクの最初の操作として、必要な <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> または <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> プロパティを明示的に設定する。  
  
-   次の `AppContextSwitchOverrides` 要素をアプリケーションの構成ファイルに追加することで、フローしない <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> および <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> の旧バージョンの動作を選択する。  
  
    ```xml  
  
    <configuration>  
        <runtime>  
            <AppContextSwitchOverrides value="Switch.System.Globalization.NoAsyncCurrentCulture=true" />  
        </runtime>  
    </configuration>  
  
    ```  
  
-   次の互換性スイッチをプログラムで設定することで、フローしない <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> および <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> の旧バージョンの動作を選択する。  
  
    ```csharp  
    AppContext.SetSwitch("Switch.System.Globalization.NoAsyncCurrentCulture", true);  
    ```  
  
    ```vb  
    AppContext.SetSwitch("Switch.System.Globalization.NoAsyncCurrentCulture", true)  
    ```  
  
## <a name="see-also"></a>関連項目  
 [変更の再ターゲット](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
