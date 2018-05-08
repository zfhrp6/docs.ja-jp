---
title: IInstallReferenceItem::GetReference メソッド
ms.date: 03/30/2017
api_name:
- IInstallReferenceItem.GetReference
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceItem::GetReference
helpviewer_keywords:
- IInstallReferenceItem::GetReference method [.NET Framework fusion]
- GetReference method [.NET Framework fusion]
ms.assetid: 8960332f-c98a-405a-ba92-7003de0c1187
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6c64b98f3b5ab0445b076b0d3bacfaa398e26f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="iinstallreferenceitemgetreference-method"></a>IInstallReferenceItem::GetReference メソッド
ポインターを取得、 [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md)これによって表される構造体[IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppRefData`  
 [out]返された`FUSION_INSTALL_REFERENCE`ポインター。  
  
 `dwFlags`  
 [入力] 将来の機能拡張に備えて予約されています。 `dwFlags` 0 (ゼロ) にする必要があります。  
  
 `pvReserved`  
 [入力] 将来の機能拡張に備えて予約されています。 `pvReserved` null 参照である必要があります。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Fusion.h  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [IInstallReferenceItem インターフェイス](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)  
 [FUSION_INSTALL_REFERENCE 構造体](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md)
