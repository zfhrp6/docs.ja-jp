---
title: GetTypeLibInfo 関数
ms.date: 03/30/2017
api_name:
- GetTypeLibInfo
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- GetTypeLibInfo
helpviewer_keywords:
- GetTypeLibInfo function [.NET Framework]
ms.assetid: a1c4d165-9bdc-4ca8-940e-292d4ffcc338
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 56a9b97f37240e385dbd1788bafea62578d687a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="gettypelibinfo-function"></a>GetTypeLibInfo 関数
確認するには、指定したタイプ ライブラリに関する情報を返します、 [TLIBATTR](https://msdn.microsoft.com/library/ms221376\(v=vs.85\).aspx)構造体。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetTypeLibInfo(  
    [in]   LPWSTR     szFile,  
    [out]  GUID      *pTypeLibID,  
    [out]  LCID      *pTypeLibLCID,  
    [out]  SYSKIND   *pTypeLibPlatform,  
    [out]  USHORT    *pTypeLibMajorVer,  
    [out]  USHORT    *pTypeLibMinorVer  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `szFile`  
 [in]タイプ ライブラリのファイル名。  
  
 `pTypeLibID`  
 [out]タイプ ライブラリの GUID です。  
  
 `pTypeLibLCID`  
 [out]タイプ ライブラリのローカリゼーション ID です。  
  
 `pTypeLibPlatform`  
 [out]A [SYSKIND](https://msdn.microsoft.com/library/ms221272\(v=vs.85\).aspx)をタイプ ライブラリのターゲットのオペレーティング システムを識別するフラグ。 一般的な値は、SYS_WIN32 SYS_WIN64 です。  
  
 `pTypeLibMajorVer`  
 [out]タイプ ライブラリのメジャー バージョン番号。 たとえば、バージョン*x.y*、メジャー バージョン番号は*x*です。  
  
 `pTypeLibMinorVer`  
 [out]タイプ ライブラリのマイナー バージョン番号。 たとえば、バージョン*x.y*、マイナー バージョン番号は*y*です。  
  
## <a name="remarks"></a>コメント  
 `GetTypeLibInfo`関数は、 [Tlbexp.exe (タイプ ライブラリ エクスポーター)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)です。 このツールは、共通言語ランタイム (CLR) アセンブリ内の型を記述するタイプ ライブラリを生成します。  
  
 任意のパラメーターが null を返します、`HRESULT`の`E_POINTER`します。 返しますそれ以外の場合、`S_OK`です。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** TlbRef.h  
  
 **ライブラリ:** TlbRef.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Tlbexp ヘルパー関数](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 [LoadTypeLibEx 関数](https://msdn.microsoft.com/library/ms221249\(v=vs.85\).aspx)
