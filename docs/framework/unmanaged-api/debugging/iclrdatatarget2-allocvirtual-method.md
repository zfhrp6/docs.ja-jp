---
title: "ICLRDataTarget2::AllocVirtual メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget2.AllocVirtual
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget2::AllocVirtual
helpviewer_keywords:
- ICLRDataTarget2::AllocVirtual method [.NET Framework debugging]
- AllocVirtual method [.NET Framework debugging]
ms.assetid: e3226230-964b-47fb-9f53-d6fdbeda1e9e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6d869b350217903dda209699f94897b70bc57132
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget2allocvirtual-method"></a>ICLRDataTarget2::AllocVirtual メソッド
このターゲット プロセスのアドレス空間内のメモリを割り当てられません共通言語ランタイム (CLR) データ アクセス サービスによって呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT AllocVirtual(  
    [in] CLRDATA_ADDRESS addr,  
    [in] ULONG32 size,  
    [in] ULONG32 typeFlags,  
    [in] ULONG32 protectFlags,  
    [out] CLRDATA_ADDRESS* virt  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `addr`  
 [in]A`CLRDATA_ADDRESS`割り当てられるメモリの要求の開始アドレスを指定する値。  
  
 `size`  
 [in]割り当てられるメモリのバイト単位のサイズ。  
  
 `typeFlags`  
 [in]メモリの割り当てを制御するフラグ。 Win32 を参照してください`VirtualAlloc`関数。  
  
 `protectFlags`  
 [in]割り当てられたメモリの保護属性。 Win32 を参照してください`VirtualAlloc`関数。  
  
 `virt`  
 [out]ポインター、`CLRDATA_ADDRESS`割り当てられたメモリの実際の開始アドレスを指定する値。  
  
## <a name="remarks"></a>コメント  
 `AllocVirtual`メソッドは、Win32 の論理ラッパーとして機能`VirtualAlloc`関数。  
  
 このメソッドは、デバッグ アプリケーションの作成者によって実装されます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** ClrData.idl、ClrData.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ICLRDataTarget2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [FreeVirtual メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)
