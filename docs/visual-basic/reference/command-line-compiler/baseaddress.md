---
title: /baseaddress
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- /baseaddress
- baseaddress
helpviewer_keywords:
- -baseaddress compiler option [Visual Basic]
- /baseaddress compiler option [Visual Basic]
- baseaddress compiler option [Visual Basic]
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8be88bf4834ca58b1fe708eb1ef7188c583fef0f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="baseaddress"></a>/baseaddress
DLL を作成するときに、既定のベース アドレスを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
/baseaddress:address  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`address`|必須です。 DLL のベース アドレス。 このアドレスは、16 進数として指定する必要があります。|  
  
## <a name="remarks"></a>コメント  
 によって、DLL の既定のベース アドレスを設定、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]です。  
  
 このアドレスの下位ワードが丸められることに注意してください。 たとえば、0x11110001 とを指定する場合はられて 0x11110000 に丸められます。  
  
 DLL の署名プロセスを完了するには、`–R`厳密名ツール (Sn.exe) のオプションです。  
  
 ターゲットが DLL ではない場合、このオプションは無視されます。  
  
|Visual Studio IDE で/baseaddress を設定するには|  
|---|  
|1.**ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。 詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。<br />2.**[コンパイル]** タブをクリックします。<br />3.**[詳細設定]** をクリックします。<br />4.値を変更、 **DLL ベース アドレス:**ボックス。 **注:** 、 **DLL ベース アドレス:**ターゲットが DLL でない限りボックスは読み取り専用です。|  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Sn.exe (厳密名ツール)](https://msdn.microsoft.com/library/k5b5tt23)
