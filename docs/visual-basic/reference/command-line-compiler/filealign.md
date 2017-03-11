---
title: "/filealign | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "sections compiler option [Visual Basic]"
  - "alignment compiler option [Visual Basic]"
  - "-filealign compiler option [Visual Basic]"
  - "section alignment"
  - "/filealign compiler option [Visual Basic]"
  - "filealign compiler option [Visual Basic]"
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# /filealign
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

出力ファイルのセクションを配置する場所を指定します。  
  
## 構文  
  
```  
/filealign:number  
```  
  
## 引数  
 `number`  
 必ず指定します。  出力ファイル内のセクションの配置を指定する値です。  有効値は、512、1024、2048、4096、および 8192 です。  これらの値はバイト単位です。  
  
## 解説  
 出力ファイル内の各セクションの配置を指定するには、`/filealign` オプションを使用します。  セクションは、エラー コードまたはデータが含まれる、ポータブル実行可能 \(PE\) ファイル内の連続するメモリのブロックです。  `/filealign` オプションでは、非標準の配置でアプリケーションをコンパイルできます。このオプションが必要になるケースは多くありません。  
  
 各セクションは、`/filealign` の値の倍数となる境界上に配置されます。  固定された既定値はありません。  `/filealign` が指定されていない場合は、コンパイラによりコンパイル時に既定値が選択されます。  
  
 セクションのサイズを指定すると、出力ファイルのサイズが変化します。  セクションのサイズの変更は、容量の小さなデバイス上で動作するプログラムに対して有効な場合があります。  
  
> [!NOTE]
>  `/filealign` オプションは Visual Studio の開発環境内からは利用できません。このオプションを利用できるのは、コマンド ラインからコンパイルするときだけです。  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)