---
title: LoadTypeLibWithResolver 関数
ms.date: 03/30/2017
api_name:
- LoadTypeLibWithResolver
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- LoadTypeLibWithResolver
helpviewer_keywords:
- LoadTypeLibWithResolver function [.NET Framework]
ms.assetid: 7123a89b-eb9b-463a-a552-a081e33b0a3a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 751794746e26bd8f0ec2cd6db2f62876e78674e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460276"
---
# <a name="loadtypelibwithresolver-function"></a>LoadTypeLibWithResolver 関数
タイプ ライブラリの読み込みを使用して、指定された[ITypeLibResolver インターフェイス](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)内部的に参照されるタイプ ライブラリを解決するのには。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `szFile`  
 [in]タイプ ライブラリのファイル パス。  
  
 `regkind`  
 [in]A [REGKIND 列挙](https://msdn.microsoft.com/library/windows/desktop/ms221159.aspx)タイプ ライブラリを登録する方法を制御するフラグ。 その有効な値は次のとおりです。  
  
-   `REGKIND_DEFAULT`: 既定の登録の動作を使用します。  
  
-   `REGKIND_REGISTER`: このタイプ ライブラリを登録します。  
  
-   `REGKIND_NONE`: このタイプ ライブラリを登録できませんしないでください。  
  
 `pTlbResolver`  
 [in]実装へのポインター、 [ITypeLibResolver インターフェイス](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)です。  
  
 `pptlib`  
 [out]読み込まれているタイプ ライブラリへの参照。  
  
## <a name="return-value"></a>戻り値  
 次の表に、HRESULT 値の 1 つ。  
  
|戻り値|説明|  
|------------------|-------------|  
|`S_OK`|成功。|  
|`E_OUTOFMEMORY`|メモリが不足しています。|  
|`E_POINTER`|1 つ以上のポインターが有効ではありません。|  
|`E_INVALIDARG`|1 つ以上の引数が有効ではありません。|  
|`TYPE_E_IOERROR`|関数は、ファイルに書き込めませんでした。|  
|`TYPE_E_REGISTRYACCESS`|システムの登録データベースは開けませんでした。|  
|`TYPE_E_INVALIDSTATE`|タイプ ライブラリを開けませんでした。|  
|`TYPE_E_CANTLOADLIBRARY`|タイプ ライブラリまたは DLL を読み込むことができませんでした。|  
  
## <a name="remarks"></a>コメント  
 [Tlbexp.exe (タイプ ライブラリ エクスポーター)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)呼び出し、`LoadTypeLibWithResolver`アセンブリをタイプ ライブラリへの変換処理中に機能します。  
  
 この関数は、レジストリに最小限のアクセス権を持つ指定したタイプ ライブラリを読み込みます。 関数は、内部的に参照されるタイプ ライブラリ、それぞれが読み込まれ、親のタイプ ライブラリに追加する必要がありますのタイプ ライブラリを調べます。  
  
 参照タイプ ライブラリを読み込むことができます、前に、ファイルの完全パスにファイルのパスを参照を解決する必要があります。 これを使用、 [ResolveTypeLib メソッド](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md)はによって提供される、 [ITypeLibResolver インターフェイス](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)に渡される、`pTlbResolver`パラメーター。  
  
 参照タイプ ライブラリの完全ファイル パスがわかっている場合、`LoadTypeLibWithResolver`関数を読み込んで、参照されるタイプ ライブラリ、親の種類をライブラリに追加、組み合わされたマスター型ライブラリを作成します。  
  
 解決されたマスター タイプ ライブラリへの参照を解決してすべての内部で参照されているタイプ ライブラリを読み込むと、関数を返します、`pptlib`パラメーター。  
  
 `LoadTypeLibWithResolver`関数一般に、 [Tlbexp.exe (タイプ ライブラリ エクスポーター)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)、独自の内部を供給する[ITypeLibResolver インターフェイス](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)での実装、 `pTlbResolver`パラメーター。  
  
 呼び出す場合`LoadTypeLibWithResolver`を直接指定する必要あります独自[ITypeLibResolver インターフェイス](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)実装します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** TlbRef.h  
  
 **ライブラリ:** TlbRef.lib  
  
 **.NET framework のバージョン:** 3.5、3.0、2.0  
  
## <a name="see-also"></a>関連項目  
 [Tlbexp ヘルパー関数](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 [LoadTypeLibEx 関数](https://msdn.microsoft.com/library/windows/desktop/ms221249\(v=vs.85\).aspx)
