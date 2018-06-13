---
title: ForwardTranslateAccelerator 関数 (WPF アンマネージ API リファレンス)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: d8a296c0590d07c4929610021714d2a257236d67
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542562"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a>ForwardTranslateAccelerator 関数 (WPF アンマネージ API リファレンス)
この API は、Windows Presentation Foundation (WPF) インフラストラクチャをサポートしてをコードから直接使用するものではありません。  
  
 Windows の管理、Windows Presentation Foundation (WPF) インフラストラクチャによって使用されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
#### <a name="parameters"></a>パラメーター  
 pMsg  
 メッセージへのポインター。  
  
 appUnhandled  
 `true` アプリが既に指定されていますが、入力メッセージの処理が、それが処理されていません。それ以外の場合、`false`です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[.NET Framework システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **DLL:**  
  
 .NET framework 3.0 および 3.5: PresentationHostDLL.dll  
  
 .NET Framework 4 以降: PresentationHost_v0400.dll  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [WPF のアンマネージ API リファレンス](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
