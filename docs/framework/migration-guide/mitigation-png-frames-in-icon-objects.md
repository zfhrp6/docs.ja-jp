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
# <a name="mitigation-png-frames-in-icon-objects"></a><span data-ttu-id="355e0-102">軽減策: Icon オブジェクトの PNG フレーム</span><span class="sxs-lookup"><span data-stu-id="355e0-102">Mitigation: PNG Frames in Icon Objects</span></span>
<span data-ttu-id="355e0-103">.NET Framework 4.6 以降では、 <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=fullName> メソッドで、PNG フレームを含んだアイコンを正常に <xref:System.Drawing.Bitmap> オブジェクトに変換できます。</span><span class="sxs-lookup"><span data-stu-id="355e0-103">Starting with the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=fullName> method successfully converts icons with PNG frames into <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 <span data-ttu-id="355e0-104">.NET Framework 4.5.2 以前のバージョンを対象としたアプリでは、 <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=fullName> オブジェクトに PNG フレームが含まれていると、 <xref:System.ArgumentOutOfRangeException> メソッドが <xref:System.Drawing.Icon> の例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="355e0-104">In apps that target the .NET Framework 4.5.2 and earlier versions, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=fullName> method throws an <xref:System.ArgumentOutOfRangeException> exception if the <xref:System.Drawing.Icon> object has PNG frames.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="355e0-105">影響</span><span class="sxs-lookup"><span data-stu-id="355e0-105">Impact</span></span>  
 <span data-ttu-id="355e0-106">この変更は、.NET Framework 4.6 を対象として再コンパイルされたアプリのうち、 <xref:System.ArgumentOutOfRangeException> オブジェクトに PNG フレームが含まれている場合は <xref:System.Drawing.Icon> をスローするように特別な処理が実装されているアプリに影響します。</span><span class="sxs-lookup"><span data-stu-id="355e0-106">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an <xref:System.Drawing.Icon> object has PNG frames.</span></span> <span data-ttu-id="355e0-107">.NET Framework 4.6 で実行している場合は、正常に変換が行われ、 <xref:System.ArgumentOutOfRangeException> がスローされることはないため、例外ハンドラーは呼び出されません。</span><span class="sxs-lookup"><span data-stu-id="355e0-107">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>  
  
### <a name="mitigation"></a><span data-ttu-id="355e0-108">軽減策</span><span class="sxs-lookup"><span data-stu-id="355e0-108">Mitigation</span></span>  
 <span data-ttu-id="355e0-109">この動作に不都合がある場合は、次に示す要素を app.config ファイルの [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) セクションに追加することで、以前の動作を維持できます。</span><span class="sxs-lookup"><span data-stu-id="355e0-109">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 <span data-ttu-id="355e0-110">app.config ファイルに既に `AppContextSwitchOverrides` 要素が含まれている場合は、次に示すように新しい値を `value` 属性にマージする必要があります。</span><span class="sxs-lookup"><span data-stu-id="355e0-110">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the `value` attribute like this:</span></span>  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;<previous key>=<previous value>" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="355e0-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="355e0-111">See Also</span></span>  
 [<span data-ttu-id="355e0-112">変更の再ターゲット</span><span class="sxs-lookup"><span data-stu-id="355e0-112">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)

