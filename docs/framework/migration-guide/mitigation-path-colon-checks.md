---
title: "軽減策: パスのコロン チェック | Microsoft Docs"
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
ms.assetid: a0bb52de-d279-419d-8f23-4b12d1a3f36e
caps.latest.revision: 5
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: b5e2426fc81c8fd38994a4124cf71af8ec445bfb
ms.contentlocale: ja-jp
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-path-colon-checks"></a>軽減策: パスのコロン チェック
[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] を対象とするアプリ以降では、以前はサポートされていなかったパスをサポートするために (長さと形式の両方について) 数多くの変更が加えられました。 具体的には、適切なドライブの区切り構文 (コロン) のチェックがより正しく行われるようになりました。  
  
## <a name="impact"></a>影響  
 これらの変更により、<xref:System.IO.Path.GetDirectoryName%2A?displayProperty=fullName> メソッドや <xref:System.IO.Path.GetPathRoot%2A?displayProperty=fullName> メソッドで以前はサポートされていた一部の URI パスがブロックされます。  
  
## <a name="mitigation"></a>軽減策  
 <xref:System.IO.Path.GetDirectoryName%2A?displayProperty=fullName> メソッドや <xref:System.IO.Path.GetPathRoot%2A?displayProperty=fullName> メソッドでサポートされなくなった、以前は受け入れられていたパスの問題を回避するには、次のようにします。  
  
-   URL からスキームを手動で削除します。 たとえば、URL から `file://` を削除します。  
  
-   <xref:System.Uri> コンストラクターに URI を渡し、<xref:System.Uri.LocalPath%2A?displayProperty=fullName> プロパティの値を取得します。  
  
-   `Switch.System.IO.UseLegacyPathHandling`<xref:System.AppContext> を `true` に切り替えて、新しいパスの正規化を無効にします。  
  
    ```xml  
    <runtime>  
        <AppContextSwitchOverrides value="Switch.System.IO.UseLegacyPathHandling=true" />    
    </runtime>  
    ```  
  
## <a name="see-also"></a>関連項目  
 [変更の再ターゲット](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-2.md)

