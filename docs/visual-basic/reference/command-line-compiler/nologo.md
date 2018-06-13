---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 011c9499eaa728588e6181e33a96dd75b4a7b84b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648542"
---
# <a name="-nologo-visual-basic"></a>-nologo (Visual Basic)
コンパイル時に著作権画面を表示および情報メッセージの表示を抑制します。  
  
## <a name="syntax"></a>構文  
  
```  
-nologo  
```  
  
## <a name="remarks"></a>コメント  
 指定した場合`-nologo`コンパイラでは、著作権の見出しは表示されません。 既定では、`-nologo` は無効です。  
  
> [!NOTE]
>  `-nologo`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。  
  
## <a name="example"></a>例  
 次のコードのコンパイル`T2.vb`著作権の見出しは表示されません。  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
