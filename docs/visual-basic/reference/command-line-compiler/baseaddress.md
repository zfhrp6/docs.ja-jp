---
title: "/baseaddress | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "/baseaddress"
  - "baseaddress"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "-baseaddress compiler option [Visual Basic]"
  - "/baseaddress compiler option [Visual Basic]"
  - "baseaddress compiler option [Visual Basic]"
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# /baseaddress
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

ダイナミック リンク ライブラリ \(DLL: Dynamic Link Library\) を作成するときの既定のベース アドレスを指定します。  
  
## 構文  
  
```  
/baseaddress:address  
```  
  
## 引数  
  
|||  
|-|-|  
|語句|定義|  
|`address`|必ず指定します。  DLL のベース アドレス。  このアドレスは 16 進数として指定する必要があります。|  
  
## 解説  
 DLL の既定のベース アドレスは、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] によって設定されます。  
  
 このアドレスの下位ワードは丸められます。  たとえば、0x11110001 と指定すると、丸められて 0x11110000 になります。  
  
 DLL の署名プロセスを完了するには、厳密名ツール \(Sn.exe\) の `–R` オプションを使用します。  
  
 ターゲットが DLL でない場合、このオプションは無視されます。  
  
||  
|-|  
|Visual Studio IDE で \/baseaddress を設定するには|  
|1.  **ソリューション エクスプローラー**でプロジェクトを選択します。  **\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  詳細については、「[Introduction to the Project Designer](http://msdn.microsoft.com/ja-jp/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。<br />2.  **\[コンパイル\]** タブをクリックします。<br />3.  **\[詳細\]** をクリックします。<br />4.  **\[DLL ベース アドレス\]** ボックス内の値を変更します。 **Note:**      **\[DLL ベース アドレス\]** ボックスは、対象が DLL である場合を除き、読み取り専用です。|  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/target](../../../visual-basic/reference/command-line-compiler/target.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Sn.exe \(厳密名ツール\)](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md)