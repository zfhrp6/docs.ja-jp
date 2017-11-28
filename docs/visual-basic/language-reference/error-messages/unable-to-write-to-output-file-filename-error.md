---
title: "出力ファイル &#39; を書き込めません。&lt;filename&gt;&#39;:&lt;エラー&gt;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31019
- bc31019
helpviewer_keywords: BC31019
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d142a8c741a9f0e25b8ac3c0002d04f437bf0ca9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="unable-to-write-to-output-file-39ltfilenamegt39-lterrorgt"></a>出力ファイル &#39; を書き込めません。&lt;filename&gt;&#39;:&lt;エラー&gt;
ファイルの作成で問題が発生しました。  
  
 出力ファイルを書き込み用に開くことができません。 ファイル (または、そのファイルが格納されているフォルダー) は、別のプロセスによって排他的に開かれているか、読み取り専用属性が設定されている可能性があります。  
  
 ファイルが排他的に開かれている一般的な原因として、次の状況が考えられます。  
  
-   このアプリケーションが既に実行されていて、ファイルを使用している。 この問題を解決するためには、アプリケーションを終了します。  
  
-   別のアプリケーションがファイルを開いている。 この問題を解決するためには、ファイルにアクセスしている他のアプリケーションがないことを確認します。 ファイルにアクセスしているアプリケーションがわからない場合があります。この場合、アプリケーションを終了する最も簡単な方法として、コンピューターの再起動が考えられます。  
  
 プロジェクトの出力ファイルのいずれか 1 つだけが読み取り専用になっている場合でも、この例外がスローされます。  
  
 **エラー ID:** BC31019  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  プログラムをもう一度コンパイルし、エラーがまだ発生するかどうか確認します。  
  
2.  エラーが引き続き発生する場合は、作業内容を保存し、[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] を再起動します。  
  
3.  エラーが引き続き発生する場合は、コンピューターを再起動します。  
  
4.  エラーがまだ発生する場合は、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] を再インストールします。  
  
5.  再インストールした後にエラーが続く場合は、マイクロソフト プロダクト サポート サービスに通知してください。  
  
### <a name="to-check-file-attributes-in-file-explorer"></a>エクスプローラーでファイル属性を確認するには  
  
1.  対象のフォルダーを開きます。  
  
2.  クリックして、**ビュー**アイコンを選択し、**詳細**です。  
  
3.  列ヘッダーを右クリックして選択**属性**ドロップダウン リストからです。  
  
### <a name="to-change-the-attributes-of-a-file-or-folder"></a>ファイルやフォルダーの属性を変更するには  
  
1.  **ファイル エクスプ ローラー**をファイルまたはフォルダーを右クリックして**プロパティ**です。  
  
2.  **属性**のセクションで、**全般**タブで、、**読み取り専用**ボックス。  
  
3.  Press **OK**.  
  
## <a name="see-also"></a>関連項目  
 [ご意見](/visualstudio/ide/talk-to-us)
