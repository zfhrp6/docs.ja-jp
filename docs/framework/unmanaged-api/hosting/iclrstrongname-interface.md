---
title: ICLRStrongName インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRStrongName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName
helpviewer_keywords:
- ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 2fac66fd-6b3b-4dbd-8baf-86038bd85526
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 92ae4c2f4a6fb126f5d86cee216e5b2bb6170e66
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436112"
---
# <a name="iclrstrongname-interface"></a>ICLRStrongName インターフェイス
厳密な名前によるアセンブリの署名の基本的なグローバル静的関数を提供します。 すべて`ICLRStrongName`メソッドは、標準の COM Hresult を返します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetHashFromAssemblyFile メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)|指定したハッシュ アルゴリズムを使用して、指定したアセンブリ ファイルのハッシュを取得します。|  
|[GetHashFromAssemblyFileW メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)|指定したハッシュ アルゴリズムを使用して、Unicode 文字列として指定したアセンブリ ファイルのハッシュを取得します。|  
|[GetHashFromBlob メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md)|指定したハッシュ アルゴリズムを使用して、指定されたメモリ アドレスのアセンブリのハッシュを取得します。|  
|[GetHashFromFile メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)|指定されたファイルの内容のハッシュを生成します。|  
|[GetHashFromFileW メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)|Unicode 文字列で指定されたファイルの内容のハッシュを生成します。|  
|[GetHashFromHandle メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)|指定したハッシュ アルゴリズムを使用して、指定したファイル ハンドルを持つファイルの内容のハッシュを生成します。|  
|[StrongNameCompareAssemblies メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)|2 つのアセンブリが厳密な名前の署名によってのみが異なるかどうかを判断します。|  
|[StrongNameFreeBuffer メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)|など、厳密な名前のメソッドを前回呼び出したときに割り当てられたメモリを解放[StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)、 [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)、または[StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md).|  
|[StrongNameGetBlob メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)|指定したアドレスに実行可能ファイルのバイナリ表現を指定したバッファーに設定します。|  
|[StrongNameGetBlobFromImage メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)|指定されたメモリ アドレスでのアセンブリ イメージのバイナリ表現を取得します。|  
|[StrongNameGetPublicKey メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)|プライベート/パブリック キーのペアから公開キーを取得します。|  
|[StrongNameHashSize メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md)|指定したハッシュ アルゴリズムを使用して、ハッシュに必要なバッファー サイズを取得します。|  
|[StrongNameKeyDelete メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)|指定したキー コンテナーを削除します。|  
|[StrongNameKeyGen メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)|厳密な名前に使用するために新しい公開/秘密キー ペアを作成します。|  
|[StrongNameKeyGenEx メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)|厳密な名前を使用して指定されたキー サイズで新しい公開/秘密キー ペアを生成します。|  
|[StrongNameKeyInstall メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)|公開/秘密キー ペアをコンテナーにインポートします。|  
|[StrongNameSignatureGeneration メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)|指定したアセンブリの厳密な名前の署名を生成します。|  
|[StrongNameSignatureGenerationEx メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)|指定したフラグに基づいて、指定したアセンブリの厳密な名前の署名を生成します。|  
|[StrongNameSignatureSize メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md)|厳密な名前の署名のサイズを返します。|  
|[StrongNameSignatureVerification メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)|指定されたパスにあるアセンブリ マニフェストに指定したフラグに従って検証される厳密な名前の署名が含まれるかどうかを示す値を取得します。|  
|[StrongNameSignatureVerificationEx メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)|指定されたパスにあるアセンブリ マニフェストに厳密な名前の署名が含まれるかどうかを示す値を取得します。|  
|[StrongNameSignatureVerificationFromImage メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)|メモリに既にマップされているアセンブリが関連付けられている公開キーの有効なことを確認します。|  
|[StrongNameTokenFromAssembly メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)|指定したアセンブリ ファイルから、厳密な名前のトークンを作成します。|  
|[StrongNameTokenFromAssemblyEx メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)|指定したアセンブリ ファイルから、厳密な名前のトークンを作成し、公開キーを返します。|  
|[StrongNameTokenFromPublicKey メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)|公開キーを表すトークンを取得します。|  
  
## <a name="remarks"></a>コメント  
 インスタンスを取得することができます、`ICLRStrongName`を呼び出して、 [iclrruntimeinfo::getinterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)メソッドを使用して`CLSID_CLRStrongName`と`IID_ICLRStrongName`パラメーターとして。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [ホスティング](../../../../docs/framework/unmanaged-api/hosting/index.md)
