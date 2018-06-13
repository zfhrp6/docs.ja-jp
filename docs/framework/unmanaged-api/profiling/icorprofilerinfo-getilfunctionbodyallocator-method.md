---
title: ICorProfilerInfo::GetILFunctionBodyAllocator メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILFunctionBodyAllocator
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILFunctionBodyAllocator
helpviewer_keywords:
- GetILFunctionBodyAllocator method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBodyAllocator method [.NET Framework profiling]
ms.assetid: 5da1bf3d-dddf-4892-b266-578ee54d570b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 00a3afab4d5f6151bcd0efd2b658d4cd7fa8f1e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33462203"
---
# <a name="icorprofilerinfogetilfunctionbodyallocator-method"></a>ICorProfilerInfo::GetILFunctionBodyAllocator メソッド
Microsoft intermediate language (MSIL) コード内のメソッドの本体を交換するために使用されるメモリを割り当てる方法を提供するインターフェイスを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetILFunctionBodyAllocator(  
    [in]  ModuleID      moduleId,  
    [out] IMethodMalloc **ppMalloc);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `moduleId`  
 [in]メソッドが含まれているモジュールの ID。  
  
 `ppMalloc`  
 [out]ポインター、 [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)メモリを割り当てる方法を提供するインターフェイスです。  
  
## <a name="remarks"></a>コメント  
 MSIL コードでメソッドの本体は、4 GB 内のモジュールに従っていることを意味、読み込まれたモジュールの基準とした相対仮想アドレス (RVA) として配置する必要があります。 メソッドの本体のスワップ アウトするためのツールを容易にできるように、`GetILFunctionBodyAllocator`メソッドにより、メモリはその範囲内で割り当てられています。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
