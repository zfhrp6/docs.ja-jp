---
title: "ファイルを TEMP に保存できません | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID735"
ms.assetid: 1055fc15-9641-43b2-a40c-a0a9fbbb34b2
caps.latest.revision: 7
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 7
---
# ファイルを TEMP に保存できません
コンポーネントが TEMP という名前のディレクトリを見つけられないか、または TEMP ディレクトリが含まれているドライブまたはパーティションには情報を保存するための十分な領域が不足しています。  
  
### このエラーを解決するには  
  
1.  "TEMP" という名前のディレクトリを作成し、そのパスに等しい TEMP 環境変数を設定します。  
  
2.  不要なファイルを消去してドライブに領域を確保するか、または別のパーティションに TEMP ディレクトリを作成し、そのパスに等しい TEMP 環境変数を設定します。  
  
## 参照  
 [Error Types](../../visual-basic/programming-guide/language-features/error-types.md)