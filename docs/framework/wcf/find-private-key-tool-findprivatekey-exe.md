---
title: "秘密キー検索ツール (FindPrivateKey.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8846a95-3fcc-4e8c-b9c0-128d975a6307
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5e2110e129b293ffb04c8e3eb69a5c3bfe83c17b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="find-private-key-tool-findprivatekeyexe"></a>秘密キー検索ツール (FindPrivateKey.exe)
このコマンド ライン ツールを使用して、証明書ストアから秘密キーを取得できます。 たとえば、FindPrivateKey.exe を使用して、証明書ストア内の特定の X.509 証明書に関連付けられている秘密キー ファイルの場所と名前を見つけることができます。  
  
> [!IMPORTANT]
>  FindPrivateKey ツールは、WCF のサンプルとして付属しています。 このサンプルの検索場所とビルド方法の詳細については、  
  
## <a name="syntax"></a>構文  
  
```  
FindPrivateKey<storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]  
```  
  
## <a name="remarks"></a>コメント  
 次の表では、秘密キー検索ツール (FindPrivateKey.exe) で使用できる引数とオプションについて説明します。  
  
|引数|説明|  
|--------------|-----------------|  
|`storeName`|証明書ストアの名前。|  
|`storeLocation`|証明書ストアの場所。|  
  
|オプション|説明|  
|------------|-----------------|  
|`/n <`*subjectName*`>`|証明書のサブジェクト名を指定します。|  
|`/t <`*拇印*`>`|証明書のサムプリントを指定します。 Certmgr.exe を使用して証明書のサムプリントを取得します。|  
|`/f`|ファイル名だけを出力します。|  
|`/d`|ディレクトリだけを出力します。|  
|`/a`|絶対ファイル名を出力します。|  
  
## <a name="examples"></a>例  
 次のコマンドは、John Doe の秘密キーを取得します。  
  
```  
FindPrivateKey My CurrentUser -n "CN=John Doe"  
```  
  
 次のコマンドは、ローカル マシンの秘密キーを取得します。  
  
```  
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –a  
```
