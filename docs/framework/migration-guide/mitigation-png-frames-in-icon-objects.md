---
title: "軽減策: Icon オブジェクトの PNG フレーム | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9d5088d70397e21cb555c78b2701960ee69bde66
ms.contentlocale: ja-jp
ms.lasthandoff: 05/22/2017

---
# <a name="mitigation-png-frames-in-icon-objects"></a>軽減策: Icon オブジェクトの PNG フレーム
.NET Framework 4.6 以降では、<xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=fullName> メソッドで、PNG フレームを含んだアイコンを正常に <xref:System.Drawing.Bitmap> オブジェクトに変換できます。  
  
 .NET Framework 4.5.2 以前のバージョンを対象としたアプリでは、<xref:System.Drawing.Icon> オブジェクトに PNG フレームが含まれていると、<xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=fullName> メソッドが <xref:System.ArgumentOutOfRangeException> の例外をスローします。  
  
## <a name="impact"></a>影響  
 この変更は、.NET Framework 4.6 を対象として再コンパイルされたアプリのうち、<xref:System.Drawing.Icon> オブジェクトに PNG フレームが含まれている場合は <xref:System.ArgumentOutOfRangeException> をスローするように特別な処理が実装されているアプリに影響します。 .NET Framework 4.6 で実行している場合は、正常に変換が行われ、<xref:System.ArgumentOutOfRangeException> がスローされることはないため、例外ハンドラーは呼び出されません。  
  
### <a name="mitigation"></a>軽減策  
 この動作に不都合がある場合は、次に示す要素を app.config ファイルの [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに追加することで、以前の動作を維持できます。  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 app.config ファイルに既に `AppContextSwitchOverrides` 要素が含まれている場合は、次に示すように新しい値を `value` 属性にマージする必要があります。  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;<previous key>=<previous value>" />  
```  
  
## <a name="see-also"></a>関連項目  
 [変更の再ターゲット](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)

