---
title: "軽減策: Icon オブジェクトの PNG フレーム"
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2115f2cec327603373ebf566b4d6ccef6404c895
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-png-frames-in-icon-objects"></a>軽減策: Icon オブジェクトの PNG フレーム
.NET Framework 4.6 以降では、 <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=fullName> メソッドで、PNG フレームを含んだアイコンを正常に <xref:System.Drawing.Bitmap> オブジェクトに変換できます。  
  
 .NET Framework 4.5.2 以前のバージョンを対象としたアプリでは、 <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=fullName> オブジェクトに PNG フレームが含まれていると、 <xref:System.ArgumentOutOfRangeException> メソッドが <xref:System.Drawing.Icon> の例外をスローします。  
  
## <a name="impact"></a>影響  
 この変更は、.NET Framework 4.6 を対象として再コンパイルされたアプリのうち、 <xref:System.ArgumentOutOfRangeException> オブジェクトに PNG フレームが含まれている場合は <xref:System.Drawing.Icon> をスローするように特別な処理が実装されているアプリに影響します。 .NET Framework 4.6 で実行している場合は、正常に変換が行われ、 <xref:System.ArgumentOutOfRangeException> がスローされることはないため、例外ハンドラーは呼び出されません。  
  
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

