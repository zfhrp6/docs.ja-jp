---
title: ICorProfilerInfo2::GetStringLayout メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStringLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStringLayout
helpviewer_keywords:
- GetStringLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetStringLayout method [.NET Framework profiling]
ms.assetid: 43189651-a535-4803-a1d1-f1c427ace2ca
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8d1bd732a82028afe809f4c2141e1d61668eae1c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454923"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a>ICorProfilerInfo2::GetStringLayout メソッド
文字列オブジェクトのレイアウトに関する情報を取得します。 このメソッドは非推奨、 [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]、によって置き換えられると、 [icorprofilerinfo 3::getstringlayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md)メソッドです。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pBufferLengthOffset`  
 [out]相対的に、位置のオフセットへのポインター、`ObjectID`ポインターは、文字列の長さを格納します。 長さとして格納されている、`DWORD`です。  
  
> [!NOTE]
>  このパラメーターは、バッファーの長さではなく、文字列、自体の長さを返します。 バッファーの長さは使用できなくします。  
  
 `PStringLengthOffset`  
 [out]相対的に、位置のオフセットへのポインター、`ObjectID`文字列自体の長さを格納するポインター。 長さとして格納されている、`DWORD`です。  
  
 `pBufferOffset`  
 [out]相対的に、バッファーのオフセットへのポインター、`ObjectID`ワイド文字の文字列を格納するポインター。  
  
## <a name="remarks"></a>コメント  
 `GetStringLayout`メソッドは、に対して相対的なオフセットを取得、`ObjectID`ポインターでは、次の格納場所の。  
  
-   文字列のバッファーの長さ。  
  
-   文字列自体の長さ。  
  
-   ワイド文字の実際の文字列を格納しているバッファー。  
  
 文字列には、null で終わる可能性があります。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
