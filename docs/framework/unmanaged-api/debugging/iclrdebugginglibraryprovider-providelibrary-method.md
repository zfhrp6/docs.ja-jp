---
title: ICLRDebuggingLibraryProvider::ProvideLibrary メソッド
ms.date: 03/30/2017
api_name:
- ICLRDebuggingLibraryProvider.ProvideLibrary Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebuggingLibraryProvider::ProvideLibrary
helpviewer_keywords:
- ProvideLibrary method [.NET Framework debugging]
- ICLRDebuggingLibraryProvider::ProvideLibrary method [.NET Framework debugging]
ms.assetid: 86f06245-9517-49be-8d8c-ca5deaf34c02
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0644258eb1622f388f55d0657c8922079fe4dc1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407241"
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a>ICLRDebuggingLibraryProvider::ProvideLibrary メソッド
コールバック インターフェイスの共通言語ランタイム (CLR) バージョン固有の上にロードし、要求時にデバッグ ライブラリをライブラリ プロバイダーを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ProvideLibrary(  
     [in] const WCHAR* pwszFileName,  
     [in] DWORD dwTimestamp,  
     [in] DWORD dwSizeOfImage,  
     [out] HMODULE* hModule);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pwszFilename`  
 [in]要求されたモジュールの名前。  
  
 `dwTimestamp`  
 [in]COFF ファイルのヘッダーの PE ファイルに格納されている日付時刻のタイムスタンプ。  
  
 `pLibraryProvider`  
 [in]`SizeOfImage` PE ファイルの COFF 省略可能なファイルのヘッダーに格納されているフィールドです。  
  
 `hModule`  
 [out]要求されたモジュールへのハンドル。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドは正常に完了しました。|  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>コメント  
 `ProvideLibrary` により、デバッガーは mscordbi.dll mscordacwks.dll などの特定の CLR ファイルのデバッグに必要なモジュールを提供します。 モジュール ハンドルが有効になるまでの呼び出しが、 [iclrdebugging::canunloadnow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md)メソッドは、これら解放される可能性があります、この時点で、ハンドルを解放する、呼び出し元の責任であることを示します。  
  
 デバッガーは、すべて使用可能な方法を使用して、検索またはデバッグのモジュールを調達する可能性があります。  
  
> [!IMPORTANT]
>  この機能は、実行可能ファイル、および可能性のある悪意のあるコードが含まれているモジュールを提供する API の呼び出し元を使用します。 セキュリティ上の予防措置として呼び出し元は、使用しないでください`ProvideLibrary`はそれ自体を実行するすべてのコードを配布します。  
>   
>  Mscordbi.dll または mscordacwks.dll などの既にリリースされてライブラリで重大なセキュリティ上の問題が検出された場合、shim にパッチできるの不適切なバージョンのファイルを認識するようにします。 Shim は、によるパッチ形式のバージョンのファイルに対する要求を発行し、すべての要求に対する応答で提供される場合は、不適切なバージョンを拒否します。 これは、shim の新しいバージョンに、ユーザーがパッチされている場合にのみに発生することができます。 未修正のバージョンは、脆弱なままです。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
