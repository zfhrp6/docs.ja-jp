---
title: "プラットフォーム呼び出しによるデータのマーシャリング | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "データ マーシャリング, プラットフォーム呼び出し"
  - "マーシャリング, プラットフォーム呼び出し"
  - "プラットフォーム呼び出し, マーシャリング (データの)"
ms.assetid: dc5c76cf-7b12-406f-b79c-d1a023ec245d
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# プラットフォーム呼び出しによるデータのマーシャリング
アンマネージ ライブラリからエクスポートされた関数を呼び出すには、.NET Framework アプリケーションで、マネージ コード内にアンマネージ関数を表す関数プロトタイプが必要です。  プラットフォーム呼び出しがデータを正しくマーシャリングできるようにするプロトタイプを作成するには、次のことを実行する必要があります。  
  
-   [DLLImportAttribute](frlrfSystemRuntimeInteropServicesDllImportAttributeClassTopic) 属性をマネージ コード内の静的関数またはメソッドに適用します。  
  
-   アンマネージ データ型をマネージ データ型に置き換えます。  
  
 アンマネージ関数に付属のドキュメントを使用して、属性とその省略可能なフィールドを適用し、アンマネージ型をマネージ データ型に置き換えることによって、同等のマネージ プロトタイプを作成できます。  **DllImportAttribute** を適用する方法について詳しくは、「[アンマネージ DLL 関数の処理](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)」を参照してください。  
  
 このセクションでは、アンマネージ ライブラリによってエクスポートされた関数に引数を渡し、その関数からの戻り値を受け取るための、マネージ関数のプロトタイプを作成する方法を示すサンプルを示します。  サンプルではまた、いつ <xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性と <xref:System.Runtime.InteropServices.Marshal> クラスを使用して明示的にデータをマーシャリングするかをも示しています。  
  
## プラットフォーム呼び出しのデータ型  
 次の表は、Win32 API \(Wtypes.h にリストされている\) と C スタイルの関数で使用されるデータ型を一覧で示しています。  多くのアンマネージ ライブラリには、これらのデータ型をパラメーターや戻り値として渡す関数が含まれています。  3 番目の列には、マネージ コードで使用する、対応する .NET Framework の組み込みの値型またはクラスを一覧で示します。  場合によっては、表にリストされた型を、同じサイズの型に置き換えることができます。  
  
|Wtypes.h でのアンマネージ型|アンマネージ C 言語型|マネージ クラス名|説明|  
|------------------------|------------------|---------------|--------|  
|**HANDLE**|**void\***|<xref:System.IntPtr?displayProperty=fullName>|32 ビット Windows オペレーティング システム、64 ビット Windows オペレーティング システムで 64 ビットに 32 ビットです。|  
|**BYTE**|**unsigned char**|<xref:System.Byte?displayProperty=fullName>|8 ビット|  
|**SHORT**|**short**|<xref:System.Int16?displayProperty=fullName>|16 ビット|  
|**WORD**|**unsigned short**|<xref:System.UInt16?displayProperty=fullName>|16 ビット|  
|**INT**|**int**|<xref:System.Int32?displayProperty=fullName>|32 ビット|  
|**UINT**|**unsigned int**|<xref:System.UInt32?displayProperty=fullName>|32 ビット|  
|**LONG**|**long**|<xref:System.Int32?displayProperty=fullName>|32 ビット|  
|**BOOL**|**long**|[\<caps:sentence id\="tgt48" sentenceid\="f5f846452032b75e5fcec49a05fe125a" class\="tgtSentence"\>System.Int32\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.byte.aspx)|32 ビット|  
|**DWORD**|**unsigned long**|<xref:System.UInt32?displayProperty=fullName>|32 ビット|  
|**ULONG**|**unsigned long**|<xref:System.UInt32?displayProperty=fullName>|32 ビット|  
|**CHAR**|**char**|<xref:System.Char?displayProperty=fullName>|ANSI で装飾します。|  
|**WCHAR**|**wchar\_t**|<xref:System.Char?displayProperty=fullName>|Unicode で装飾します。|  
|**LPSTR**|**char\***|<xref:System.String?displayProperty=fullName> または <xref:System.Text.StringBuilder?displayProperty=fullName>|ANSI で装飾します。|  
|**LPCSTR**|**Const char\***|<xref:System.String?displayProperty=fullName> または <xref:System.Text.StringBuilder?displayProperty=fullName>|ANSI で装飾します。|  
|**LPWSTR**|**wchar\_t\***|<xref:System.String?displayProperty=fullName> または <xref:System.Text.StringBuilder?displayProperty=fullName>|Unicode で装飾します。|  
|**LPCWSTR**|**Const wchar\_t\***|<xref:System.String?displayProperty=fullName> または <xref:System.Text.StringBuilder?displayProperty=fullName>|Unicode で装飾します。|  
|**FLOAT**|**浮動小数点型**|<xref:System.Single?displayProperty=fullName>|32 ビット|  
|**DOUBLE**|**倍精度浮動小数点型**|<xref:System.Double?displayProperty=fullName>|64 ビット|  
  
 [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)]、C\#、および C\+\+ での対応する型については、「[.NET Framework クラス ライブラリの概要](../../../docs/standard/class-library-overview.md)」を参照してください。  
  
## PinvokeLib.dll  
 次のコードでは、Pinvoke.dll によって提供されるライブラリ関数を定義します。  このセクションで説明される多くのサンプルでは、このライブラリを呼び出します。  
  
### 例  
 [!code-cpp[PInvokeLib#1](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.cpp#1)]  
  
 [!code-cpp[PInvokeLib#2](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.h#2)]