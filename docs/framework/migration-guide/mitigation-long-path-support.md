---
title: "軽減策: 長いパスのサポート"
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
ms.assetid: 3cbe2d77-6e2c-4665-a6c5-7000b9ad6890
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 138e96c3d45b79ccf30f6a3d39f0af26a48c0117
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-long-path-support"></a>軽減策: 長いパスのサポート
[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 以降を対象とするアプリでは、パスまたは完全修飾ファイル名が 260 (または `MAX_PATH`) 文字を超える場合、ファイル システムの I/O メソッドで自動的に <xref:System.IO.PathTooLongException> がスローされなくなりました。 代わりに、最大 32K の文字の長いパスがサポートされます。  
  
## <a name="impact"></a>影響  
 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] を対象として再コンパイルされたアプリのうち、パスが 260 文字を超えたために以前は <xref:System.IO.PathTooLongException> を自動的にスローしていたアプリが、次の条件下でのみ <xref:System.IO.PathTooLongException> をスローするようになります。  
  
-   パスの長さが <xref:System.Int16.MaxValue?displayProperty=fullName> (32,767) 文字を超えている。  
  
-   オペレーティング システムが `COR_E_PATHTOOLONG` またはそれと同等のものを返す。  
  
 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] 以前を対象とするアプリの従来の動作では、パスが 260 文字を超えるたびにランタイムで自動的に <xref:System.IO.PathTooLongException> がスローされていました。  
  
## <a name="mitigation"></a>軽減策  
 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] を対象とするアプリでは、長いパスのサポートが望ましくない場合、app.config ファイルの [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに次の行を追加することでサポートを無効にできます。  
  
```xml  
<runtime>   
   <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=true" />   
</runtime>  
```  
  
 以前のバージョンの .NET Framework を対象とするものの、[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 以降で実行されているアプリでは、app.config ファイルの [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに次の行を追加することで、長いパスのサポートを有効にできます。  
  
```xml  
<runtime>   
   <AppContextSwitchOverrides value="Switch.System.IO.BlockLongPaths=false" />   
</runtime>  
```  
  
## <a name="see-also"></a>関連項目  
 [変更の再ターゲット](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)

