---
title: "Classes Used in .NET Framework File I/O and the File System (Visual Basic) | Microsoft Docs"
ms.custom: ""
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
  - "file I/O classes"
ms.assetid: 4a5ca924-eea8-4a95-a5f0-6ac10de276a3
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# Classes Used in .NET Framework File I/O and the File System (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

以下の表は、.NET Framework のファイル I\/O で一般的に使用するクラスの一覧です。ファイル I\/O クラス、ストリームの作成に使用するクラス、ストリームの読み取りと書き込みに使用するクラスに分類されています。  
  
 [!INCLUDE[dnprdnlong](../../../../csharp/programming-guide/events/includes/dnprdnlong-md.md)] ドキュメントで詳細な一覧を参照するには、「[クラス ライブラリの概要](../Topic/.NET%20Framework%20Class%20Library%20Overview.md)」を参照してください。  
  
## ファイル、ドライブ、およびディレクトリ用の基本 I\/O クラス  
 次の表は、ファイル I\/O に使用する主要なクラスの一覧とその説明です。  
  
|Class|Description|  
|-----------|-----------------|  
|<xref:System.IO.Directory?displayProperty=fullName>|ディレクトリやサブディレクトリを作成、移動、および反復処理するための静的メソッドを提供します。|  
|<xref:System.IO.DirectoryInfo?displayProperty=fullName>|ディレクトリやサブディレクトリを作成、移動、および反復処理するためのインスタンス メソッドを提供します。|  
|<xref:System.IO.DriveInfo?displayProperty=fullName>|ドライブを作成、移動、および反復処理するためのインスタンス メソッドを提供します。|  
|<xref:System.IO.File?displayProperty=fullName>|ファイルを作成、コピー、削除、移動、およびオープンするための静的メソッドを提供し、また `FileStream` の作成を支援します。|  
|<xref:System.IO.FileAccess?displayProperty=fullName>|読み取り専用、書き込み専用、読み取り\/書き込みの各ファイル アクセスの定数を定義します。|  
|<xref:System.IO.FileAttributes?displayProperty=fullName>|`Archive`、`Hidden`、`ReadOnly` など、ファイルおよびディレクトリの属性を提供します。|  
|<xref:System.IO.FileInfo?displayProperty=fullName>|ファイルを作成、コピー、削除、移動、およびオープンするための静的メソッドを提供し、また `FileStream` の作成を支援します。|  
|<xref:System.IO.FileMode?displayProperty=fullName>|ファイルを開く方法を制御します。  このパラメーターは、`FileStream` および `IsolatedStorageFileStream` の数多くのコンストラクターで、および <xref:System.IO.File> と <xref:System.IO.FileInfo> の `Open`メソッドで指定します。|  
|<xref:System.IO.FileShare?displayProperty=fullName>|他のファイル ストリームが同一のファイルに対して行うことができるアクセスの種類を制御するための定数を定義します。|  
|<xref:System.IO.Path?displayProperty=fullName>|ディレクトリ文字列を処理するためのメソッドとプロパティを提供します。|  
|<xref:System.Security.Permissions.FileIOPermission?displayProperty=fullName>|<xref:System.Security.Permissions.FileIOPermissionAttribute.Read%2A>、<xref:System.Security.Permissions.FileIOPermissionAttribute.Write%2A>、<xref:System.Security.Permissions.FileIOPermissionAttribute.Append%2A>、および <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> の各アクセス許可を定義し、ファイルおよびフォルダーへのアクセスを制御します。|  
  
## ストリームの作成に使用するクラス  
 次の表は、ストリームの作成に使用する主要なクラスの一覧とその説明です。  
  
|Class|Description|  
|-----------|-----------------|  
|<xref:System.IO.BufferedStream?displayProperty=fullName>|他のストリームの読み取りおよび書き込み操作に対しバッファリング層を追加します。|  
|<xref:System.IO.FileStream?displayProperty=fullName>|<xref:System.IO.FileStream.Seek%2A> メソッドによってファイルへのランダム アクセスをサポートします。  <xref:System.IO.FileStream> は、既定では同期的にファイルを開きますが、非同期操作もサポートします。|  
|<xref:System.IO.MemoryStream?displayProperty=fullName>|バッキング ストアがファイルではなくメモリであるストリームを作成します。|  
|<xref:System.Net.Sockets.NetworkStream?displayProperty=fullName>|ネットワーク アクセスの基になるデータ ストリームを提供します。|  
|<xref:System.Security.Cryptography.CryptoStream?displayProperty=fullName>|データ ストリームを暗号化方式にリンクするストリームを定義します。|  
  
## ストリームの読み取りと書き込みに使用するクラス  
 次の表は、ストリームによるファイルの読み取りと書き込みに使用する固有のクラスの一覧です。  
  
|**Class**|**Description**|  
|---------------|---------------------|  
|<xref:System.IO.BinaryReader?displayProperty=fullName>|エンコードされた文字列とプリミティブ データ型を <xref:System.IO.FileStream> から読み取ります。|  
|<xref:System.IO.BinaryWriter?displayProperty=fullName>|エンコードされた文字列とプリミティブ データ型を <xref:System.IO.FileStream> に書き込みます。|  
|<xref:System.IO.StreamReader?displayProperty=fullName>|<xref:System.IO.StreamReader.CurrentEncoding%2A> を使用して文字とバイト間の変換を行い、<xref:System.IO.FileStream> から文字を読み取ります。  <xref:System.IO.StreamReader> には、<xref:System.IO.StreamReader.CurrentEncoding%2A> 固有のプリアンブル \(バイト順マークなど\) があるかどうかに応じて、指定したストリームに適した <xref:System.IO.StreamReader.CurrentEncoding%2A> を確認するコンストラクターがあります。|  
|<xref:System.IO.StreamWriter?displayProperty=fullName>|`FileStream` に文字を書き込みます。その際、<xref:System.IO.StreamWriter.Encoding%2A> を使用して、文字をバイトに変換します。|  
|<xref:System.IO.StringReader?displayProperty=fullName>|`String` から文字を読み取ります。  出力は、任意のエンコーディングのストリームまたは `String` のいずれかです。|  
|<xref:System.IO.StringWriter?displayProperty=fullName>|`String` に文字を書き込みます。  出力は、任意のエンコーディングのストリームまたは `String` のいずれかです。|  
  
## 参照  
 [ストリームの構成](../Topic/Composing%20Streams.md)   
 [ファイルおよびストリーム入出力](../Topic/File%20and%20Stream%20I-O.md)   
 [非同期ファイル I\/O](../Topic/Asynchronous%20File%20I-O.md)   
 [.NET Framework のファイル I\/O とファイル システムの基礎 \(Visual Basic\)](../../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)