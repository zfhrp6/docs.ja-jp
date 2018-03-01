---
title: "FormatFromRawValue 関数 (アンマネージ API リファレンス)"
description: "FormatFromRawValue 関数では、生のパフォーマンス データを指定した形式に変換します。"
ms.date: 11/21/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- FormatFromRawValue
api_location:
- PerfCounter.dll
api_type:
- DLLExport
f1_keywords:
- FormatFromRawValue
helpviewer_keywords:
- FormatFromRawValue function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3daa89ec0b40bb9c08898ecd682f05f0f0ce09a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="formatfromrawvalue-function"></a>FormatFromRawValue 関数
形式の変換が時間ベースの場合は、指定された形式に 1 つの生のパフォーマンス データの値または生のパフォーマンス データの 2 つの値に変換します。   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>構文  
  
```  
int FormatFromRawValue (
   [in] uint                    dwCounterType, 
   [in] uint                    dwFormat, 
   [in] long*                   pTimeBase,
   [in] PDH_RAW_COUNTER*        pRawValue1,
   [in] PDH_RAW_COUNTER*        pRawValue2,
   [out] PDH_FMT_COUNTERVALUE*  pFmtValue
); 
```  

## <a name="parameters"></a>パラメーター

`dwCounterType`  
[in]カウンターの型。 カウンターの種類の一覧は、次を参照してください。 [WMI パフォーマンス カウンターの種類](https://msdn.microsoft.com/library/aa394569(v=vs.85).aspx)です。 `dwCounterType`以外の場合は、どのカウンター型でもかまいません`PERF_LARGE_RAW_FRACTION`と`PERF_LARGE_RAW_BASE`です。 

`dwFormat`  
[in]生のパフォーマンス データを変換先形式です。 次の値のいずれかを指定できます。

|定数  |[値]  |説明 |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |0x00000200 | 倍精度浮動小数点値として計算された値を返します。 | 
| `PDH_FMT_LARGE` | 0x00000400 | 計算される値を 64 ビット整数として返します。 |
| `PDH_FMT_LONG` | 0x00000100 | 計算される値を 32 ビット整数として返します。 |

次のスケーリングのフラグのいずれかの論理和は以前の値のいずれかのことができます。

|定数  |[値]  |説明 |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | 0x00001000 | カウンターのスケール ファクターは適用されません。 |
| `PDH_FMT_1000` | 0x00002000 | 1,000 最終的な値を乗算します。 | 

`pTimeBase`  
[in]形式の変換が必要な場合、時間ベースへのポインター。 時間ベースの情報は、形式変換の必要はありません、このパラメーターの値は無視されます。

`pRawValue1`[in]ポインター、 [ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx)生のパフォーマンスの値を表す構造です。

`pRawValue2`[in]ポインター、 [ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx)を 2 番目の生のパフォーマンス値を表す構造です。 このパラメーターを指定する場合は、2 番目の生のパフォーマンス値が必要ではありません、`null`です。

`pFmtValue`[out]ポインター、 [ `PDH_FMT_COUNTERVALUE` ](https://msdn.microsoft.com/library/windows/desktop/aa373050(v=vs.85).aspx)書式設定されたパフォーマンスの値を受け取る。

## <a name="return-value"></a>戻り値

この関数では、次の値が返されます。

|定数  |[値]  |説明  |
|---------|---------|---------|
| `ERROR_SUCCESS` | 0 | 関数呼び出しが成功します。 |
| `PDH_INVALID_ARGUMENT` | 0xC0000BBD | 必須の引数は、見つからないか正しくないです。 | 
| `PDH_INVALID_HANDLE` | 0xC0000BBC | ハンドルが有効な PDH オブジェクトではありません。 |
  
## <a name="remarks"></a>コメント

この関数への呼び出しをラップする、 [FormatFromRawValue](https://msdn.microsoft.com/library/ms231047(v=vs.85).aspx)関数。

## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ライブラリ:** PerfCounter.dll  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目  
[WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
