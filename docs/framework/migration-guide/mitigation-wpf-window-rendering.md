---
title: "軽減策: WPF ウィンドウのレンダリング | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
caps.latest.revision: 3
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c911513551e9629a4a6975762c1952c73c50f733
ms.contentlocale: ja-jp
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-wpf-window-rendering"></a>軽減策: WPF ウィンドウのレンダリング
Windows 8 以上で実行している [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] では、マルチ モニターのシナリオで 1 つのディスプレイの外部にウィンドウを拡張すると、ウィンドウ全体がクリッピングなしでレンダリングされます。  
  
## <a name="impact"></a>影響  
 一般に、複数のモニターで、クリッピングなしでウィンドウ全体を表示することが期待の動作です。 ただし、Windows 7 以前のバージョンでは、2 つ目のモニターにウィンドウの一部をレンダリングするとパフォーマンスに大きな影響があるため、WPF ウィンドウが 1 つのディスプレイの外部に拡張されるときにはクリッピングされます。  
  
 Windows 8 以上で複数のモニターに WPF ウィンドウをレンダリングする際の詳細な影響は、多数の要因に依存しているために、正確に数量化することはできません。 場合によっては、グラフィックを多用するアプリケーションを実行するユーザーや複数のモニターに及ぶウィンドウを使用するユーザーの場合は特に、依然としてパフォーマンスに望ましくない影響が生じることがあります。 または、.NET Framework の複数のバージョン間で一貫性のある動作が実現できれば十分な場合もあります 。  
  
## <a name="mitigation"></a>軽減策  
 この変更を無効にして、WPF ウィンドウが 1 つのディスプレイを超える場合にクリッピングされるという、以前の動作に戻すこともできます。 これには、2 つの方法があります。  
  
-   `<EnableMultiMonitorDisplayClipping>` 要素をアプリケーションの構成ファイルの `<appSettings>` セクションに追加することにより、Windows 8 以降で実行中のアプリケーションでこの動作を無効にしたり有効にしたりすることができます。 たとえば、次の構成セクションにより、クリッピングなしのレンダリングが無効になります。  
  
    ```  
  
    <appSettings>  
        <add key="EnableMultiMonitorDisplayClipping" value="true"/>  
      </appSettings>  
  
    ```  
  
     `<EnableMultiMonitorDisplayClipping>` 構成設定には、次の 2 つの値のいずれかを指定できます。  
  
    -   `true` を指定すると、レンダリングの際にウィンドウをモニターの境界でクリッピングすることを有効にします。  
  
    -   `false` を指定すると、レンダリングの際にウィンドウをモニターの境界でクリッピングすることを無効にします。  
  
-   アプリの起動時に <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> プロパティを `true` に設定します。  
  
## <a name="see-also"></a>関連項目  
 [ランタイムの変更点](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
