---
title: /nologo (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3c2c7e7a111a3763d7463f67c2d984955da33bbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="nologo-visual-basic"></a>/nologo (Visual Basic)
コンパイル時に著作権画面を表示および情報メッセージの表示を抑制します。  
  
## <a name="syntax"></a>構文  
  
```  
/nologo  
```  
  
## <a name="remarks"></a>コメント  
 指定した場合`/nologo`コンパイラでは、著作権の見出しは表示されません。 既定では、`/nologo` は無効です。  
  
> [!NOTE]
>  `/nologo`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。  
  
## <a name="example"></a>例  
 次のコードのコンパイル`T2.vb`著作権の見出しは表示されません。  
  
```  
vbc /nologo t2.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
