---
title: "定数と列挙型 (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- enumerations [Visual Basic]
- constants
- constants, list of
ms.assetid: 309c0ad5-83e4-4f96-99ea-83cd95107417
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e37ef2e3c51e96e85cb214054195016e69d52382
ms.lasthandoff: 03/13/2017

---
# <a name="constants-and-enumerations-visual-basic"></a>定数と列挙型 (Visual Basic)
[!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]定義済みの定数および開発者のための列挙体の番号を提供します。 定数は、アプリケーションの実行全体で一定に保たれる値を格納します。 列挙体は、関連する定数を使用して作業し、名前の定数値を関連付ける便利な方法を提供します。  
  
## <a name="constants"></a>定数  
  
### <a name="conditional-compilation-constants"></a>条件付きコンパイル定数  
 次の表は、条件付きコンパイルで使用できる定義済みの定数を示します。  
  
|**定数**|**説明**|  
|---|---|  
|`CONFIG`|現在の設定に対応する文字列、**アクティブ ソリューション構成**ボックスに、 **Configuration Manager**します。|  
|`DEBUG`|A`Boolean`で設定できる値、**プロジェクトのプロパティ** ダイアログ ボックス。 既定では、プロジェクトのデバッグ構成を定義`DEBUG`します。 `DEBUG`が定義されている<xref:System.Diagnostics.Debug>クラスのメソッドへの出力を生成する、**出力**ウィンドウ</xref:System.Diagnostics.Debug>。 定義されていない場合<xref:System.Diagnostics.Debug>クラスのメソッドはコンパイルされず、デバッグの出力は生成されません</xref:System.Diagnostics.Debug>。|  
|`TARGET`|出力の種類のプロジェクトまたはコマンドラインの設定を表す文字列**/target**オプション。 有効な値`TARGET`は。<br /><br /> -Windows アプリケーション用には、「ため」です。<br />-コンソール アプリケーション用には、"exe"です。<br />クラス ライブラリには、"library"です。<br />-モジュールの場合に、「モジュール」です。<br />- **/Target**オプションを設定することがあります、[!INCLUDE[vsprvs](../../csharp/includes/vsprvs_md.md)]統合開発環境です。 詳細については、次を参照してください。 [/target (Visual Basic)](../../visual-basic/reference/command-line-compiler/target.md)します。|  
|`TRACE`|A`Boolean`で設定できる値、**プロジェクトのプロパティ** ダイアログ ボックス。 既定では、プロジェクトのすべての構成を定義する`TRACE`です。 `TRACE`が定義されている<xref:System.Diagnostics.Trace>クラスのメソッドへの出力を生成する、**出力**ウィンドウ</xref:System.Diagnostics.Trace>。 定義されていない場合<xref:System.Diagnostics.Trace>クラスのメソッドはコンパイルされず、いいえ`Trace`出力が生成されます</xref:System.Diagnostics.Trace>。|  
|`VBC_VER`|表す数値、[!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]バージョンで、*メジャー*.*マイナー*形式です。 バージョン番号[!INCLUDE[vbprvblong](../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]8.0 は、です。|  
  
### <a name="print-and-display-constants"></a>印刷と表示の定数  
 印刷を呼び出す関数を表示すると、実際の値の代わりに、コードで、次の定数を使用することができます。  
  
|**定数**|**説明**|  
|---|---|  
|`vbCrLf`|復帰/改行文字の組み合わせ。|  
|`vbCr`|キャリッジ リターン文字。|  
|`vbLf`|ライン フィード文字。|  
|`vbNewLine`|改行文字です。|  
|`vbNullChar`|Null 文字です。|  
|`vbNullString`|同じ長さ&0; の文字列ではありません ("") です。外部プロシージャを呼び出すために使用します。|  
|`vbObjectError`|エラー番号。 ユーザー定義のエラー番号は、この値よりも大きくする必要があります。 例:<br /><br /> `Err.Raise(Number) = vbObjectError + 1000`|  
|`vbTab`|タブ文字。|  
|`vbBack`|バック スペース文字です。|  
|`vbFormFeed`|Microsoft Windows では使用されません。|  
|`vbVerticalTab`|Microsoft Windows では有効ではないです。|  
  
## <a name="enumerations"></a>列挙  
 次の表をによって提供される列挙体について説明[!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]します。  
  
|列挙|説明|  
|---|---|  
|<xref:Microsoft.VisualBasic.AppWinStyle></xref:Microsoft.VisualBasic.AppWinStyle>|呼び出すときに、プログラムの起動に使用するウィンドウ スタイルを示す、<xref:Microsoft.VisualBasic.Interaction.Shell%2A>関数</xref:Microsoft.VisualBasic.Interaction.Shell%2A>。|  
|<xref:Microsoft.VisualBasic.AudioPlayMode></xref:Microsoft.VisualBasic.AudioPlayMode>|オーディオのメソッドを呼び出すときにサウンドを再生する方法を示します。|  
|<xref:Microsoft.VisualBasic.ApplicationServices.BuiltInRole></xref:Microsoft.VisualBasic.ApplicationServices.BuiltInRole>|呼び出すときにチェックするロールの種類を示す、<xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A>メソッド</xref:Microsoft.VisualBasic.ApplicationServices.User.IsInRole%2A>。|  
|<xref:Microsoft.VisualBasic.CallType></xref:Microsoft.VisualBasic.CallType>|呼び出すときに呼び出されるプロシージャの種類を示す、<xref:Microsoft.VisualBasic.Interaction.CallByName%2A>関数</xref:Microsoft.VisualBasic.Interaction.CallByName%2A>。|  
|<xref:Microsoft.VisualBasic.CompareMethod></xref:Microsoft.VisualBasic.CompareMethod>|比較関数を呼び出すときに文字列を比較する方法を示します。|  
|<xref:Microsoft.VisualBasic.DateFormat></xref:Microsoft.VisualBasic.DateFormat>|日付を表示する方法を示すを呼び出すときに、<xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>関数</xref:Microsoft.VisualBasic.Strings.FormatDateTime%2A>。|  
|<xref:Microsoft.VisualBasic.DateInterval></xref:Microsoft.VisualBasic.DateInterval>|日付関連の関数を呼び出すときに使用する、日付の間隔の決定方法と形式の設定方法を示します。|  
|<xref:Microsoft.VisualBasic.FileIO.DeleteDirectoryOption></xref:Microsoft.VisualBasic.FileIO.DeleteDirectoryOption>|どうすればよいのディレクトリを削除するには、ファイルまたはディレクトリが含まれている場合を指定します。|  
|<xref:Microsoft.VisualBasic.DueDate></xref:Microsoft.VisualBasic.DueDate>|支払期日を示します財務メソッドを呼び出すとき。|  
|<xref:Microsoft.VisualBasic.FileIO.FieldType></xref:Microsoft.VisualBasic.FileIO.FieldType>|テキスト フィールドが区切られているかどうか、または固定幅を示します。|  
|<xref:Microsoft.VisualBasic.FileAttribute></xref:Microsoft.VisualBasic.FileAttribute>|ファイル アクセス関数を呼び出すときに使用するファイル属性を示します。|  
|<xref:Microsoft.VisualBasic.FirstDayOfWeek></xref:Microsoft.VisualBasic.FirstDayOfWeek>|日付に関連する関数を呼び出すときに使用する週の最初の日を示します。|  
|<xref:Microsoft.VisualBasic.FirstWeekOfYear></xref:Microsoft.VisualBasic.FirstWeekOfYear>|日付関連の関数を呼び出すときに使用するには、年度の第&1; 週を示します。|  
|<xref:Microsoft.VisualBasic.MsgBoxResult></xref:Microsoft.VisualBasic.MsgBoxResult>|によって返される、メッセージ ボックスに押されたボタンを示す、<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>関数</xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>。|  
|<xref:Microsoft.VisualBasic.MsgBoxStyle></xref:Microsoft.VisualBasic.MsgBoxStyle>|呼び出すときに表示するボタンを示す、<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>関数</xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>。|  
|<xref:Microsoft.VisualBasic.OpenAccess></xref:Microsoft.VisualBasic.OpenAccess>|ファイル アクセスの関数を呼び出すときに、ファイルを開く方法を示します。|  
|<xref:Microsoft.VisualBasic.OpenMode></xref:Microsoft.VisualBasic.OpenMode>|ファイル アクセスの関数を呼び出すときに、ファイルを開く方法を示します。|  
|<xref:Microsoft.VisualBasic.OpenShare></xref:Microsoft.VisualBasic.OpenShare>|ファイル アクセスの関数を呼び出すときに、ファイルを開く方法を示します。|  
|<xref:Microsoft.VisualBasic.FileIO.RecycleOption></xref:Microsoft.VisualBasic.FileIO.RecycleOption>|ファイルを完全に削除またはごみ箱に移動するかどうかを指定します。|  
|<xref:Microsoft.VisualBasic.FileIO.SearchOption></xref:Microsoft.VisualBasic.FileIO.SearchOption>|すべてを検索するかどうかを指定または最上位のディレクトリのみです。|  
|<xref:Microsoft.VisualBasic.TriState></xref:Microsoft.VisualBasic.TriState>|示す、`Boolean`値または数値書式指定の関数を呼び出すときに既定値を使用する必要がありますか。|  
|<xref:Microsoft.VisualBasic.FileIO.UICancelOption></xref:Microsoft.VisualBasic.FileIO.UICancelOption>|指定する必要があります、ユーザーがクリックした場合に実行**キャンセル**操作中にします。|  
|<xref:Microsoft.VisualBasic.FileIO.UIOption></xref:Microsoft.VisualBasic.FileIO.UIOption>|コピー、削除、またはファイルやディレクトリを移動するときに、進行状況 ダイアログを表示するかどうかを指定します。|  
|<xref:Microsoft.VisualBasic.VariantType></xref:Microsoft.VisualBasic.VariantType>|によって返されるバリアント型のオブジェクトの種類を示す、<xref:Microsoft.VisualBasic.Information.VarType%2A>関数</xref:Microsoft.VisualBasic.Information.VarType%2A>。|  
|<xref:Microsoft.VisualBasic.VbStrConv></xref:Microsoft.VisualBasic.VbStrConv>|呼び出すときに実行する変換の種類を示す、<xref:Microsoft.VisualBasic.Strings.StrConv%2A>関数</xref:Microsoft.VisualBasic.Strings.StrConv%2A>。|  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic 言語リファレンス](../../visual-basic/language-reference/index.md)   
 [Visual Basic](../../visual-basic/index.md)   
 [定数の概要](../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)   
 [列挙型の概要](../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
