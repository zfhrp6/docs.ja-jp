---
title: "Unable to write to output file &#39;&lt;filename&gt;&#39;: &lt;error&gt; | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc31019"
  - "bc31019"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC31019"
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# Unable to write to output file &#39;&lt;filename&gt;&#39;: &lt;error&gt;
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

ファイルの作成で問題が発生しました。  
  
 出力ファイルを書き込み用に開くことができません。  ファイル \(または、そのファイルが格納されているフォルダー\) は、別のプロセスによって排他的に開かれているか、読み取り専用属性が設定されている可能性があります。  
  
 ファイルが排他的に開かれている一般的な原因として、次の状況が考えられます。  
  
-   このアプリケーションが既に実行されていて、ファイルを使用している。  この問題を解決するためには、アプリケーションを終了します。  
  
-   別のアプリケーションがファイルを開いている。  この問題を解決するためには、ファイルにアクセスしている他のアプリケーションがないことを確認します。  ファイルにアクセスしているアプリケーションがわからない場合があります。この場合、アプリケーションを終了する最も簡単な方法として、コンピューターの再起動が考えられます。  
  
 プロジェクトの出力ファイルのいずれか 1 つだけが読み取り専用になっている場合でも、この例外がスローされます。  
  
 **Error ID:** BC31019  
  
### このエラーを解決するには  
  
1.  プログラムをもう一度コンパイルし、エラーがまだ発生するかどうか確認します。  
  
2.  エラーが引き続き発生する場合は、作業内容を保存し、[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] を再起動します。  
  
3.  エラーが引き続き発生する場合は、コンピューターを再起動します。  
  
4.  エラーがまだ発生する場合は、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] を再インストールします。  
  
5.  再インストールした後にエラーが続く場合は、マイクロソフト プロダクト サポート サービスに通知してください。  
  
### エクスプローラーでファイル属性を確認するには  
  
1.  対象のフォルダーを開きます。  
  
2.  **\[表示\]** アイコンをクリックし、**\[詳細\]** を選択します。  
  
3.  列ヘッダーを右クリックして、ドロップダウン リストから **\[属性\]** を選択します。  
  
### ファイルやフォルダーの属性を変更するには  
  
1.  **\[エクスプローラー\]** でファイルまたはフォルダーを右クリックし、**\[プロパティ\]** を選択します。  
  
2.  **\[全般\]** タブの **\[属性\]** セクションにある **\[読み取り専用\]** チェック ボックスをオフにします。  
  
3.  **\[OK\]** をクリックします。  
  
## 参照  
 [ご意見](/visual-studio/ide/talk-to-us)