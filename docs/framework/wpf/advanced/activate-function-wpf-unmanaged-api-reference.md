---
title: 関数をアクティブ化する (WPF アンマネージ API リファレンス)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- Acrivate
api_location:
- PresentationHost_v0400.dll
ms.assetid: 1400329c-b598-465f-80f2-e3dabf044811
ms.openlocfilehash: 4931f64a525f14ad5b0b69c582a81cd15d98e541
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539054"
---
# <a name="activate-function-wpf-unmanaged-api-reference"></a>関数をアクティブ化する (WPF アンマネージ API リファレンス)
この API は、Windows Presentation Foundation (WPF) インフラストラクチャをサポートしてをコードから直接使用するものではありません。  
  
 Windows の管理、Windows Presentation Foundation (WPF) インフラストラクチャによって使用されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
void Activate(  
    const ActivateParameters* pParameters,  
    __deref_out_ecount(1) LPUNKNOWN* ppInner,  
    );  
```  
  
#### <a name="parameters"></a>パラメーター  
 pParameters  
 ウィンドウのアクティブ化パラメーターへのポインター。  
  
 ppInner  
 ポインターを格納している 1 つの要素のバッファーのアドレスへのポインター、<xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument>オブジェクト。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[.NET Framework システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **DLL:**  
  
 .NET framework 3.0 および 3.5: PresentationHostDLL.dll  
  
 .NET Framework 4 以降: PresentationHost_v0400.dll  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [WPF のアンマネージ API リファレンス](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
