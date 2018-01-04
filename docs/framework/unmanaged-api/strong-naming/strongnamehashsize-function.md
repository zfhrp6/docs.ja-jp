---
title: "StrongNameHashSize 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameHashSize
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameHashSize
helpviewer_keywords: StrongNameHashSize function [.NET Framework strong naming]
ms.assetid: 738c98d7-a60c-45fe-a296-220af05e6991
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 20a0d5fc284dde7b127f1f177a448a95701ac8b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamehashsize-function"></a>StrongNameHashSize 関数
指定したハッシュ アルゴリズムを使用して、ハッシュに必要なバッファー サイズを取得します。  
  
 この関数は廃止されました。 使用して、 [iclrstrongname::strongnamehashsize](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md)メソッド代わりにします。  
  
## <a name="syntax"></a>構文  
  
```  
BOOLEAN StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ulHashAlg`  
 [in]バッファー サイズを計算するために使用するハッシュ アルゴリズム。  
  
 `pcbSize`  
 [out]返されたバッファーのサイズ (バイト)。  
  
## <a name="return-value"></a>戻り値  
 `true`正常に終了します。それ以外の場合、`false`です。  
  
## <a name="remarks"></a>コメント  
 場合、`StrongNameHashSize`関数が正常に完了、呼び出すしていない、 [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)最後に生成されたエラーを取得します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** StrongName.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [StrongNameHashSize メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md)  
 [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
