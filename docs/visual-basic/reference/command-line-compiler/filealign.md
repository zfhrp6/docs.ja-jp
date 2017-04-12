---
title: "/filealign |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 18d5c3e327e2e41f4786eda6c3e981125f87389d
ms.lasthandoff: 03/13/2017

---
# <a name="filealign"></a>/filealign
出力ファイルでセクションをアラインするサイズを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
/filealign:number  
```  
  
## <a name="arguments"></a>引数  
 `number`  
 必須です。 出力ファイルにセクションの配置を指定する値。 有効な値は、512、1024、2048、4096、8192 です。 これらの値はバイト単位です。  
  
## <a name="remarks"></a>コメント  
 使用することができます、`/filealign`出力ファイルのセクションの配置を指定するオプションです。 セクションは、コードまたはデータを含むポータブル実行可能 (PE) ファイル内の連続したメモリ ブロックです。 `/filealign`オプションを使用して、非標準の配置を使用してアプリケーションをコンパイルできます。 ほとんどの開発者は、このオプションを使用する必要はありません。  
  
 各セクションがの倍数では境界に合わせて調整、`/filealign`値。 固定の既定値はありません。 場合`/filealign`が指定されていない、コンパイラがコンパイル時に、既定値を選択します。  
  
 セクションのサイズを指定すると、出力ファイルのサイズを変更できます。 セクションのサイズを変更するには、小さなデバイスで実行されるプログラムに対して有効な可能性があります。  
  
> [!NOTE]
>  `/filealign`オプションは、Visual Studio 開発環境内から使用できません。 コマンドラインからコンパイルする場合だけに利用可能になります。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
