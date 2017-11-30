---
title: /filealign
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dbabc19c85501b97ef5443a6f6e12524f8de7d91
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="filealign"></a>/filealign
出力ファイルでセクションをアラインするサイズを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
/filealign:number  
```  
  
## <a name="arguments"></a>引数  
 `number`  
 必須です。 出力ファイルにセクションのアラインメントを指定する値。 有効値は 512、1024、2048、4096、および 8192 です。 これらの値はバイト単位です。  
  
## <a name="remarks"></a>コメント  
 使用することができます、`/filealign`出力ファイルのセクションのアラインメントを指定するにはオプションです。 セクションは、コードまたはデータを含むポータブル実行可能 (PE) ファイルの連続したメモリのブロックです。 `/filealign`オプションを使用して、非標準の配置を使用してアプリケーションをコンパイルできます。 ほとんどの開発者は、このオプションを使用する必要はありません。  
  
 各セクションでは、の倍数である境界に整列されます、`/filealign`値。 固定の既定値はありません。 場合`/filealign`が指定されていない、コンパイラがコンパイル時に、既定値を選択します。  
  
 セクションのサイズを指定すると、出力ファイルのサイズを変更することができます。 セクションのサイズ変更は、比較的小さなデバイスで実行されるプログラムに対して有効な場合があります。  
  
> [!NOTE]
>  `/filealign`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
