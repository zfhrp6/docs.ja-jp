---
title: "ResolveTypeLib メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ResolveTypeLib
api_location: tlbref.dll
f1_keywords: ResolveTypeLib
helpviewer_keywords:
- ITypeLibResolver::ResolveTypeLib method [.NET Framework]
- ResolveTypeLib method [.NET Framework]
ms.assetid: 95d2aa0d-8eeb-4a9f-a216-5249f7e2c167
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b668610f50c32373790130def17928b8b3b3d8b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="resolvetypelib-method"></a>ResolveTypeLib メソッド
完全修飾パスを返すことによって、タイプ ライブラリの簡易名を解決します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ResolveTypeLib(  
    [in]  BSTR      bstrSimpleName,  
    [in]  GUID      tlbid,  
    [in]  LCID      lcid,  
    [in]  USHORT    wMajorVersion,  
    [in]  USHORT    wMinorVersion,  
    [in]  SYSKIND   syskind,  
    [out] BSTR     *pbstrResolvedTlbName);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `bstrSimpleName`  
 [in]A [BSTR](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228)タイプ ライブラリの簡易名を格納しています。  
  
 `tlbid`  
 [in]レジストリでタイプ ライブラリに割り当てられた GUID です。  
  
 `lcid`  
 [in]タイプ ライブラリのローカリゼーション ID です。  
  
 `wMajorVersion`  
 [in]タイプ ライブラリのメジャー バージョン番号。 たとえば、バージョン*x.y*、メジャー バージョン番号は*x*です。  
  
 `wMinorVersion`  
 [in]タイプ ライブラリのマイナー バージョン番号。 たとえば、バージョン*x.y*、マイナー バージョン番号は*y*です。  
  
 `syskind`  
 [in]A [SYSKIND](http://msdn.microsoft.com/en-us/662048b2-59a8-48ca-9e4f-2f9a5306faa1)を運用環境を識別するフラグ。 一般的な値は、SYS_WIN32 SYS_WIN64 です。  
  
 `pbstrResolvedTlbName`  
 [out]ポインター、 [BSTR](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228)という名前で、タイプ ライブラリの完全なパスを含む、`bstrSimpleName`パラメーター。  
  
## <a name="remarks"></a>コメント  
 `ResolveTypeLib`メソッドによって呼び出されます、 [LoadTypeLibWithResolver 関数](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md)中に[Tlbexp.exe (タイプ ライブラリ エクスポーター)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)を処理します。  
  
 このインターフェイスのカスタム実装を返す必要があります、 [BSTR](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228)という名前で、タイプ ライブラリの完全なパスを含む、`bstrSimpleName`パラメーター。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** TlbRef.idl、TlbRef.h  
  
 **ライブラリ:** TlbRef.lib  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [Tlbexp ヘルパー関数](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 [LoadTypeLibEx](http://msdn.microsoft.com/en-us/56a7f9e1-810b-4a42-aa4d-691f4304f5ef)
