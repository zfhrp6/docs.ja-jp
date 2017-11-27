---
title: "厳密な名前付け (アンマネージ API リファレンス)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- strong naming [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], strong naming
- unmanaged API reference [.NET Framework], strong naming
ms.assetid: 428c68b6-a7b4-44be-b280-75905f46612c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 86d741a16a0293892d0d6d90f1763d744ed3675d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="strong-naming-unmanaged-api-reference"></a>厳密な名前付け (アンマネージ API リファレンス)
厳密な名前付け API では、クライアントが厳密な名前のアセンブリの署名を管理できるようにします。  
  
 厳密な名前を使用してアセンブリに署名すると、アセンブリ マニフェストを格納しているファイルに公開キー暗号化が追加されます。 厳密な名前の署名には、名前の一意性を確認するのに役立ち、名前の悪用を防止し、参照が解決されたときに、一意の id を持つ呼び出し元を提供します。 ただし、信頼レベルが関連付けられていない、厳密な名前です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [厳密な名前付けグローバル静的関数](http://msdn.microsoft.com/en-us/efa715df-e8cc-48f2-9ec4-26586f0dc8d0)  
 厳密な名前付け API で使用されるアンマネージ グローバル静的関数をについて説明します。  
  
> [!NOTE]
>  これらの関数のすべてが削除されてから始まる、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]です。 推奨される代替方法については、次を参照してください。、 [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)インターフェイスです。  
  
 [GetHashFromAssemblyFile 関数](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromassemblyfile-function.md)  
 指定したハッシュ アルゴリズムを使用して、指定したアセンブリ ファイルのハッシュを取得します。 推奨されなくなった、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。  
  
 [GetHashFromAssemblyFileW 関数](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromassemblyfilew-function.md)  
 指定したハッシュ アルゴリズムを使用して、Unicode 文字列として指定したアセンブリ ファイルのハッシュを取得します。 推奨されなくなった、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。  
  
 [GetHashFromBlob 関数](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromblob-function.md)  
 指定したハッシュ アルゴリズムを使用して、指定されたメモリ アドレスのアセンブリのハッシュを取得します。 推奨されなくなった、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。  
  
 [GetHashFromFile 関数](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md)  
 指定されたファイルの内容のハッシュを生成します。  推奨されなくなった、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。  
  
 [GetHashFromFileW 関数](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md)  
 Unicode 文字列で指定されたファイルの内容のハッシュを生成します。 推奨されなくなった、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。  
  
 [GetHashFromHandle 関数](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromhandle-function.md)  
 指定したハッシュ アルゴリズムを使用して、指定したファイル ハンドルを持つファイルの内容のハッシュを生成します。  推奨されなくなった、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。  
  
 [StrongNameCompareAssemblies 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamecompareassemblies-function.md)  
 2 つのアセンブリが厳密な名前の署名によってのみが異なるかどうかを判断します。 推奨されなくなった、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。  
  
 [StrongNameErrorInfo 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)  
 厳密な名前の関数のいずれかによって発生した最後のエラー コードを取得します。  
  
 [StrongNameFreeBuffer 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)  
 など、厳密な名前の関数を前回呼び出したときに割り当てられたメモリを解放[StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)、 [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md)、または[StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).   推奨されなくなった、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。  
  
 [StrongNameGetBlob 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetblob-function.md)  
 指定したアドレスに実行可能ファイルのバイナリ表現を指定したバッファーに設定します。 推奨されなくなった、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。  
  
 [StrongNameGetBlobFromImage 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetblobfromimage-function.md)  
 指定されたメモリ アドレスでのアセンブリ イメージのバイナリ表現を取得します。 推奨されなくなった、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。  
  
 [StrongNameGetPublicKey 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)  
 プライベート/パブリック キーのペアから公開キーを取得します。 推奨されなくなった、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。  
  
 [StrongNameHashSize 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamehashsize-function.md)  
 指定したハッシュ アルゴリズムを使用して、ハッシュに必要なバッファー サイズを取得します。  推奨されなくなった、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。  
  
 [StrongNameKeyDelete 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md)  
 指定したキー コンテナーを削除します。 推奨されなくなった、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。  
  
 [StrongNameKeyGen 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeygen-function.md)  
 厳密な名前に使用するために新しい公開/秘密キー ペアを作成します。  推奨されなくなった、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。  
  
 [StrongNameKeyGenEx 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeygenex-function.md)  
 厳密な名前を使用して指定されたキー サイズで新しい公開/秘密キー ペアを生成します。 推奨されなくなった、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。  
  
 [StrongNameKeyInstall 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md)  
 公開/秘密キー ペアをコンテナーにインポートします。  推奨されなくなった、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。  
  
 [StrongNameSignatureGeneration 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)  
 指定したアセンブリの厳密な名前の署名を生成します。   推奨されなくなった、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。  
  
 [StrongNameSignatureGenerationEx 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegenerationex-function.md)  
 指定したフラグに基づいて、指定したアセンブリの厳密な名前の署名を生成します。    推奨されなくなった、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。  
  
 [StrongNameSignatureSize 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md)  
 厳密な名前の署名のサイズを返します。 推奨されなくなった、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。  
  
 [StrongNameSignatureVerification 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md)  
 指定されたパスにあるアセンブリ マニフェストに指定したフラグに従って検証される厳密な名前の署名が含まれるかどうかを示す値を取得します。 推奨されなくなった、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。  
  
 [StrongNameSignatureVerificationEx 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverificationex-function.md)  
 指定されたパスにあるアセンブリ マニフェストに厳密な名前の署名が含まれるかどうかを示す値を取得します。  推奨されなくなった、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。  
  
 [StrongNameSignatureVerificationFromImage 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverificationfromimage-function.md)  
 メモリに既にマップされているアセンブリが関連付けられている公開キーの有効なことを確認します。 推奨されなくなった、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。  
  
 [StrongNameTokenFromAssembly 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md)  
 指定したアセンブリ ファイルから、厳密な名前のトークンを作成します。  推奨されなくなった、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。  
  
 [StrongNameTokenFromAssemblyEx 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassemblyex-function.md)  
 指定したアセンブリ ファイルから、厳密な名前のトークンを作成し、公開キーを返します。 推奨されなくなった、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。  
  
 [StrongNameTokenFromPublicKey 関数](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md)  
 公開キーを表すトークンを取得します。 推奨されなくなった、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。  
  
 [厳密な名前付け構造体](http://msdn.microsoft.com/en-us/4b041a2f-fd12-4b91-aacd-bc3b34a5124d)  
 厳密な名前のアセンブリの署名を管理する厳密な名前付け API を使用するアンマネージ構造体について説明します。  
  
 [PublicKeyBlob 構造体](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 バイナリ形式で公開/秘密キーのペアの公開キーを表します。  
  
## <a name="see-also"></a>関連項目  
 [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 [アンマネージ API リファレンス](../../../../docs/framework/unmanaged-api/index.md)
