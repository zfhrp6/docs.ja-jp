---
title: "Constants and Enumerations (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "enumerations [Visual Basic]"
  - "constants"
  - "constants, list of"
ms.assetid: 309c0ad5-83e4-4f96-99ea-83cd95107417
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Constants and Enumerations (Visual Basic)
[!INCLUDE[vs2017banner](../../visual-basic/developing-apps/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] には、定義済みの定数および列挙型が開発者向けに多数用意されています。  定数に格納された値は、アプリケーションの実行中に変わることはありません。  複数の関連する定数を操作する場合や、複数の定数値に名前を関連付ける場合は、列挙型を使うと便利です。  
  
## 定数  
  
### 条件付きコンパイル定数  
 条件付きコンパイルで利用できる定義済みの定数の一覧を次の表に示します。  
  
|||  
|-|-|  
|**定数**|**Description**|  
|`CONFIG`|**構成マネージャー**の **\[アクティブ ソリューション構成\]** ボックスの、現在の設定に対応する文字列|  
|`DEBUG`|**\[プロジェクトのプロパティ\]** ダイアログ ボックスで設定できる `Boolean` 値  既定では、プロジェクトの Debug 構成により、`DEBUG` が定義されます。  `DEBUG` を定義すると、<xref:System.Diagnostics.Debug> クラスのメソッドは**出力**ウィンドウに出力を生成します。  DEBUG を定義しない場合、<xref:System.Diagnostics.Debug> クラスのメソッドはコンパイルされず、デバッグ出力も生成されません。|  
|`TARGET`|プロジェクトの出力の種類、またはコマンド ラインの **\/target** オプションの設定を表す文字列  `TARGET` には、次の値を指定できます。<br /><br /> -   Windows アプリケーション用の "winexe"<br />-   コンソール アプリケーション用の "exe"<br />-   クラス ライブラリ用の "library"<br />-   モジュール用の "module"<br />-   [!INCLUDE[vsprvs](../../csharp/includes/vsprvs-md.md)] 統合開発環境では、**\/target** オプションを設定できます。  詳細については、「[\/target](../../visual-basic/reference/command-line-compiler/target.md)」を参照してください。|  
|`TRACE`|**\[プロジェクトのプロパティ\]** ダイアログ ボックスで設定できる `Boolean` 値  既定では、プロジェクトのすべての構成により、`TRACE` が定義されます。  `TRACE` を定義すると、<xref:System.Diagnostics.Trace> クラスのメソッドは**出力**ウィンドウに出力を生成します。  定義しない場合、<xref:System.Diagnostics.Trace> クラスのメソッドはコンパイルされず、`Trace` 出力も生成されません。|  
|`VBC_VER`|*major*.*minor* 形式で、[!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] バージョンを表す数。  [!INCLUDE[vbprvblong](../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)] のバージョン番号は 8.0 です。|  
  
### 印刷と表示の定数  
 印刷および表示の関数を呼び出すときに、実際の値の代わりにコード内で次の定数を使用できます。  
  
|||  
|-|-|  
|**定数**|**Description**|  
|`vbCrLf`|キャリッジ リターン文字とライン フィード文字の組み合わせ。|  
|`vbCr`|キャリッジ リターン文字。|  
|`vbLf`|ライン フィード文字。|  
|`vbNewLine`|改行文字。|  
|`vbNullChar`|Null 文字。|  
|`vbNullString`|長さ 0 の文字列 \(""\) とは異なります。外部プロシージャを呼び出す場合に使用します。|  
|`vbObjectError`|エラー番号。  ユーザー定義のエラー番号は、この値を超える値にする必要があります。  次に例を示します。<br /><br /> `Err.Raise(Number) = vbObjectError + 1000`|  
|`vbTab`|タブ文字。|  
|`vbBack`|バックスペース文字。|  
|`vbFormFeed`|Microsoft Windows では使用されていません。|  
|`vbVerticalTab`|Microsoft Windows では使用できません。|  
  
## 列挙型  
 [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] で提供されている列挙型について、次の表で説明します。  
  
|||  
|-|-|  
|列挙型|Description|  
|<xref:Microsoft.VisualBasic.AppWinStyle>|<xref:Microsoft.VisualBasic.Interaction.Shell%2A> 関数を呼び出すときに、実行されるプログラムで使用するウィンドウ スタイルを示します。|  
|<xref:Microsoft.VisualBasic.AudioPlayMode>|オーディオ関連のメソッドを呼び出すときに、サウンドの再生方法を示します。|  
|<xref:Microsoft.VisualBasic.ApplicationServices.BuiltInRole>|<xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A> メソッドを呼び出すときに、チェックするロールの種類を示します。|  
|<xref:Microsoft.VisualBasic.CallType>|<xref:Microsoft.VisualBasic.Interaction.CallByName%2A> 関数を呼び出すときに呼び出すプロシージャの種類を示します。|  
|<xref:Microsoft.VisualBasic.CompareMethod>|比較関数を呼び出すときに、文字列を比較する方法を示します。|  
|<xref:Microsoft.VisualBasic.DateFormat>|<xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A> 関数を呼び出すときに、日付の表示方法を示します。|  
|<xref:Microsoft.VisualBasic.DateInterval>|日付関連の関数を呼び出すときに、日付の間隔の決定方法および形式を示します。|  
|<xref:Microsoft.VisualBasic.FileIO.DeleteDirectoryOption>|削除対象のディレクトリ内にファイルまたはディレクトリが存在する場合の処理を指定します。|  
|<xref:Microsoft.VisualBasic.DueDate>|財務関連のメソッドを呼び出すときに、支払い期日を示します。|  
|<xref:Microsoft.VisualBasic.FileIO.FieldType>|テキスト フィールドが区切られているのか、固定幅なのかを示します。|  
|<xref:Microsoft.VisualBasic.FileAttribute>|ファイル アクセス用の関数を呼び出すときに、使用するファイル属性を示します。|  
|<xref:Microsoft.VisualBasic.FirstDayOfWeek>|日付関連の関数を呼び出すときに使用する、1 週間の最初の日を示します。|  
|<xref:Microsoft.VisualBasic.FirstWeekOfYear>|日付関連の関数を呼び出すときに使用する、1 年の最初の週を示します。|  
|<xref:Microsoft.VisualBasic.MsgBoxResult>|メッセージ ボックスで押されたボタンを示します。<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 関数から返されます。|  
|<xref:Microsoft.VisualBasic.MsgBoxStyle>|<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 関数を呼び出すときに、表示するボタンを示します。|  
|<xref:Microsoft.VisualBasic.OpenAccess>|ファイル アクセス用の関数を呼び出すときにファイルを開く方法を示します。|  
|<xref:Microsoft.VisualBasic.OpenMode>|ファイル アクセス用の関数を呼び出すときにファイルを開く方法を示します。|  
|<xref:Microsoft.VisualBasic.OpenShare>|ファイル アクセス用の関数を呼び出すときにファイルを開く方法を示します。|  
|<xref:Microsoft.VisualBasic.FileIO.RecycleOption>|ファイルを完全に削除するのか、ごみ箱に入れるのかを指定します。|  
|<xref:Microsoft.VisualBasic.FileIO.SearchOption>|すべてのディレクトリまたは最上位レベルのディレクトリの、いずれを探索するのかを指定します。|  
|<xref:Microsoft.VisualBasic.TriState>|数値書式指定関数を呼び出すときに、ブール \(`Boolean`\) 値、または既定の設定を使用するかどうかを示します。|  
|<xref:Microsoft.VisualBasic.FileIO.UICancelOption>|操作中にユーザーが **\[キャンセル\]** ボタンをクリックしたときに実行する処理を指定します。|  
|<xref:Microsoft.VisualBasic.FileIO.UIOption>|ファイルまたはディレクトリをコピー、削除、または移動するときに、プログレス ダイアログ ボックスを表示するかどうかを指定します。|  
|<xref:Microsoft.VisualBasic.VariantType>|<xref:Microsoft.VisualBasic.Information.VarType%2A> 関数が返すバリアント オブジェクトの型を示します。|  
|<xref:Microsoft.VisualBasic.VbStrConv>|<xref:Microsoft.VisualBasic.Strings.StrConv%2A> 関数を呼び出すときに実行する変換の種類を示します。|  
  
## 参照  
 [Visual Basic Language Reference](../../visual-basic/language-reference/index.md)   
 [Visual Basic](../../visual-basic/index.md)   
 [Constants Overview](../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [Enumerations Overview](../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)