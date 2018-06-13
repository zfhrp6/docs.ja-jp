---
title: ICorProfilerInfo::SetILInstrumentedCodeMap メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetILInstrumentedCodeMap method [.NET Framework profiling]
ms.assetid: bce1dcf8-b4ec-4e73-a917-f2df1ad49c8a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8ecb80de1ae46b072df4bab8357e78e7a22ae298
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458066"
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a>ICorProfilerInfo::SetILInstrumentedCodeMap メソッド
指定した Microsoft intermediate language (MSIL) マップ エントリを使用して、指定された関数のコード マップを設定します。  
  
> [!NOTE]
>  呼び出し、.NET Framework version 2.0 で`SetILInstrumentedCodeMap`上、`FunctionID`ジェネリックは、特定のアプリケーション ドメインで機能を表しますが、アプリケーション ドメインでは、その関数のすべてのインスタンスに影響することです。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetILInstrumentedCodeMap(  
    [in]  FunctionID functionId,  
    [in]  BOOL       fStartJit,  
    [in]  ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `functionId`  
 [in]コード マップを設定する対象の関数の ID。  
  
 `fStartJit`  
 [in]示すブール値かどうかを呼び出し、`SetILInstrumentedCodeMap`メソッドは、特定の 1 つ目`FunctionID`です。 設定`fStartJit`に`true`最初の呼び出しで`SetILInstrumentedCodeMap`の指定された`FunctionID`、および`false`以降。  
  
 `cILMapEntries`  
 [in]内の要素の数、`cILMapEntries`配列。  
  
 `rgILMapEntries`  
 [in]COR_IL_MAP 構造体の配列、それぞれ指定する MSIL のオフセット。  
  
## <a name="remarks"></a>コメント  
 プロファイラーは、(たとえば、指定されたソース行に達したときに通知する場合など) には、そのメソッドをインストルメント化するために多くの場合、メソッドのソース コード内のステートメントを挿入します。 `SetILInstrumentedCodeMap` プロファイラーは、元の MSIL 命令を新しい場所にマップを有効にします。 プロファイラーを使用できる、 [icorprofilerinfo::getiltonativemapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)ネイティブ オフセットを指定するため、元の MSIL オフセットを取得します。  
  
 デバッガーには、古い各オフセットが MSIL、元の未変更の MSIL コード内でオフセットを指すことと、新しいオフセットが、新しいでインストルメント化されたコード内の MSIL オフセットを指すことが前提としています。 マップは、昇順で並べ替えられます必要があります。 正常に動作するステップ実行、次のガイドラインに従ってください。  
  
-   インストルメント化された MSIL コードを並べ替えないでください。  
  
-   元の MSIL コードを削除しないでください。  
  
-   マップ内のプログラム データベース (PDB) ファイルからのすべてのシーケンス ポイントのエントリを含めます。 存在しないエントリを補間、マップは行いません。 そのため、次のマップを指定します。  
  
     (新しい 0、0)  
  
     (新しい 5、10)  
  
     (新しい 9、20)  
  
    -   0、1、2、3、または 4 の古いオフセットは、新しいオフセット 0 にマップされます。  
  
    -   古いオフセットが 5、6、7、または 8 は、新しいオフセット 10 にマップされます。  
  
    -   9 以降の古いオフセットは、新しいオフセット 20 にマップされます。  
  
    -   0、1、2、3、4、5、6、7、8、または 9 の新しいオフセットは、古いオフセット 0 にマップされます。  
  
    -   10、11、12、13、14、15、16、17、18 または 19 の新しいオフセットは、古いオフセット 5 にマップされます。  
  
    -   20 以上の新しいオフセットは、古いオフセット 9 にマップされます。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
