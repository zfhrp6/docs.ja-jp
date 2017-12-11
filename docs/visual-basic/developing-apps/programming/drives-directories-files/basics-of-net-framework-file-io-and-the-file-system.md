---
title: ".NET Framework のファイル I/O とファイル システムの基礎 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- file access, file I/O in Visual Basic
- file attributes, determining
- streams, fundamental operations
- file permissions
- streams
- streams, definition
ms.assetid: 49d837c0-cf28-416f-8606-4d83d7b479ef
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 53bd56647d04c40c44a240edcd084f0719c3d4aa
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/09/2017
---
# <a name="basics-of-net-framework-file-io-and-the-file-system-visual-basic"></a>.NET Framework のファイル I/O とファイル システムの基礎 (Visual Basic)
<xref:System.IO> 名前空間のクラスは、ドライブ、ファイル、ディレクトリの操作に使用されます。  
  
 <xref:System.IO> 名前空間には <xref:System.IO.File> クラスと <xref:System.IO.Directory> クラスが含まれています。これらのクラスを使用すると、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] でファイルとディレクトリを操作できます。 これらのオブジェクトのメソッドは静的メンバーまたは共有メンバーなので、あらかじめクラスのインスタンスを作成しなくてもメンバーを直接使用できます。 これらのクラスに関連するクラスとして、<xref:System.IO.FileInfo> クラスと <xref:System.IO.DirectoryInfo> クラスがあります。`My` 機能を使用しているユーザーには使い慣れたクラスです。 これらのクラスを使用するには、名前を完全修飾するか、または、関係するコードの先頭に `Imports` ステートメントを記述して、適切な名前空間をインポートする必要があります。 詳細については、「[Imports ステートメント (.NET 名前空間および型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)」を参照してください。  
  
> [!NOTE]
>  このセクションのそのほかのトピックでは `My.Computer.FileSystem` のクラスではなく、 `System.IO` オブジェクトを使用して、ドライブ、ファイル、およびディレクトリを操作します。 `My.Computer.FileSystem` オブジェクトは [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] のプログラムで使用する主な目的としています。 `System.IO` のクラスは [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] をサポートする [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] などの言語で使用するためのものです。  
  
## <a name="definition-of-a-stream"></a>ストリームの定義  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] では、ファイルに対する読み取りと書き込みをサポートするストリームを使用できます。 ストリームとは、1 次元の連続したデータの集まりと考えることができます。ストリームには先頭と末尾があり、カーソルでストリーム内での現在の位置を示します。  
  
 ![Filestream 内の現在位置を示すカーソル。] (../../../../visual-basic/developing-apps/programming/drives-directories-files/media/filestream.gif "FileStream")  
  
## <a name="stream-operations"></a>ストリームの操作  
 ストリームに格納されているデータは、メモリ、ファイル、または TCP/IP ソケットから取得したものです。 ストリームに対しては、次の基本操作を実行できます。  
  
-   読み取り。 ストリームを読み取ったり、文字列やバイト配列などのデータ構造にストリームからデータを転送したりできます。  
  
-   **書き込み**。 ストリームに書き込んだり、データ ソースからストリームにデータを転送したりできます。  
  
-   **シーク**。 ストリーム内の現在の位置をクエリおよび変更できます。  
  
 詳細については、「 [Composing Streams](../../../../../docs/standard/io/composing-streams.md)」を参照してください。  
  
## <a name="types-of-streams"></a>ストリームの種類  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] では、ストリームは <xref:System.IO.Stream> クラスで表されます。これは、その他のすべてのストリームのための抽象クラスです。 <xref:System.IO.Stream> クラスのインスタンスを直接作成することはできません。これを実装するいずれかのクラスを使用する必要があります。  
  
 ストリームにはさまざまな種類がありますが、ファイルの入出力 (I/O) を処理するという目的のために最も重要なのは、ファイルに対する読み取りと書き込みを実現する <xref:System.IO.FileStream> クラスと、分離ストレージに対するファイルやディレクトリの作成を実現する <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> クラスです。 この他、ファイル I/O を処理する場合、以下のようなストリームを使用できます。  
  
-   <xref:System.IO.BufferedStream>  
  
-   <xref:System.Security.Cryptography.CryptoStream>  
  
-   <xref:System.IO.MemoryStream>  
  
-   <xref:System.Net.Sockets.NetworkStream>。  
  
 次の表は、ストリームで一般的に実行するタスクの一覧です。  
  
|目的|参照トピック|
|---|---|   
|データ ファイルに対する読み取りと書き込み|[方法: 新しく作成されたデータ ファイルに対して読み書きする](../../../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)|  
|ファイルのテキストの読み取り|[方法: ファイルからテキストを読み取る](../../../../../docs/standard/io/how-to-read-text-from-a-file.md)|  
|テキストのファイルへの書き込み|[方法: ファイルにテキストを書き込む](../../../../../docs/standard/io/how-to-write-text-to-a-file.md)|  
|文字列からの文字の読み取り|[方法: 文字列から文字を読み取る](../../../../../docs/standard/io/how-to-read-characters-from-a-string.md)|  
|文字列への文字の書き込み|[方法: 文字列に文字を書き込む](../../../../../docs/standard/io/how-to-write-characters-to-a-string.md)|  
|データの暗号化|[データの暗号化](../../../../../docs/standard/security/encrypting-data.md)|  
|データの復号化|[データの復号化](../../../../../docs/standard/security/decrypting-data.md)|  
  
## <a name="file-access-and-attributes"></a>ファイル アクセスと属性  
 ファイルの作成、オープン、および共有の方法は、<xref:System.IO.FileAccess>、<xref:System.IO.FileMode>、および <xref:System.IO.FileShare> の各列挙体で制御できます。これらの列挙体には、<xref:System.IO.FileStream> クラスのコンストラクターで使用するフラグが含まれています。 たとえば、<xref:System.IO.FileStream> を開くかまたは新規作成するときに、ファイルを追加書き込み用に開くかどうか、指定のファイルが存在しない場合にファイルを新規作成するかどうか、ファイルを上書きするかどうか、などを <xref:System.IO.FileMode> 列挙体で指定できます。  
  
 <xref:System.IO.FileAttributes> 列挙体を使用すると、ファイル固有の情報を収集できます。 <xref:System.IO.FileAttributes> 列挙体は、格納されているファイルの属性を返します。これらの属性によって、圧縮ファイル、暗号化されたファイル、隠しファイル、読み取り専用ファイル、アーカイブ、ディレクトリ、システム ファイル、一時ファイルであるかどうかがわかります。  
  
 次の表は、ファイル アクセスとファイル属性に関連するタスクの一覧です。  
  
|目的|参照トピック|  
|---|---|
|ログ ファイルのオープンとテキストの追加|[方法: ログ ファイルを開いて情報を追加する](../../../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)|  
|ファイルの属性の判断|<xref:System.IO.FileAttributes>|  
  
## <a name="file-permissions"></a>ファイルのアクセス許可  
 ファイルおよびディレクトリに対するアクセスの制御は、<xref:System.Security.Permissions.FileIOPermission> クラスで行うことができます。 これは、Web フォームの開発者には特に重要な場合があります。既定では、Web フォームは、ASPNET という名前の特別なローカル ユーザー アカウントのコンテキストで実行されます。ASPNET は、[!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] および [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] のインストール時に作成されます。 ASPNET ユーザー アカウントはアクセス許可が制限されているため、アプリケーションがリソースへのアクセスを要求したときに、ユーザーが処理を実行できない場合があります (たとえば、Web アプリケーションからファイルへの書き込みなど)。 詳細については、[セキュリティのアクセス許可](http://msdn.microsoft.com/en-us/b03757b4-e926-4196-b738-3733ced2bda0)に関するページと <xref:System.Security.Permissions.FileIOPermission> に関するページを参照してください。  
  
## <a name="isolated-file-storage"></a>分離ファイル ストレージ  
 分離ストレージとは、ファイルを扱うときに、必要なアクセス許可をユーザーまたはコードが持っていないために生じる問題を解決するためのものです。 分離ストレージでは、各ユーザーにデータ コンパートメントが割り当てられます。このデータ コンパートメントには、1 つまたは複数のストアを保持できます。 ストア間は、ユーザーおよびアセンブリごとに分離できます。 ストアにアクセスできるのは、それを作成したユーザーおよびアセンブリのみです。 ストアは、完全な仮想ファイル システムとして機能します。つまり、ストア内でディレクトリやファイルを作成および操作できます。  
  
 次の表は、分離ファイル ストレージに一般に関連するタスクの一覧です。  
  
|目的|参照トピック|
|---|---|  
|分離ストアの作成|[方法: 分離ストレージでストアを取得する](../../../../../docs/standard/io/how-to-obtain-stores-for-isolated-storage.md)|  
|分離ストアの列挙|[方法: 分離ストレージでストアを列挙する](../../../../../docs/standard/io/how-to-enumerate-stores-for-isolated-storage.md)|  
|分離ストアの削除|[方法: 分離ストレージでストアを削除する](../../../../../docs/standard/io/how-to-delete-stores-in-isolated-storage.md)|  
|分離ストレージのファイルまたはディレクトリの作成|[方法: 分離ストレージでファイルおよびディレクトリを作成する](../../../../../docs/standard/io/how-to-create-files-and-directories-in-isolated-storage.md)|  
|分離ストレージのファイルの検索|[方法: 分離ストレージ内でファイルおよびディレクトリを検索する](../../../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md)|  
|分離ストレージのファイルに対する読み取りと書き込み|[方法: 分離ストレージ内でファイルの読み取りと書き込みを行う](../../../../../docs/standard/io/how-to-read-and-write-to-files-in-isolated-storage.md)|  
|分離ストレージのファイルまたはディレクトリの削除|[方法: 分離ストレージでファイルおよびディレクトリを削除する](../../../../../docs/standard/io/how-to-delete-files-and-directories-in-isolated-storage.md)|  
  
## <a name="file-events"></a>ファイルのイベント  
 <xref:System.IO.FileSystemWatcher> コンポーネントを使用すると、自システム上のファイルとディレクトリ、またはネットワークでアクセスできる任意のコンピューター上のファイルとディレクトリの変更を監視できます。 たとえば、ファイルが変更されたときに、その旨をユーザーに警告することが必要な場合があります。 変更が行われると、1 つまたは複数のイベントが発生し、バッファーに格納され、<xref:System.IO.FileSystemWatcher> コンポーネントに渡されて処理されます。  
  
## <a name="see-also"></a>関連項目  
 [ストリームの構成](../../../../../docs/standard/io/composing-streams.md)  
 [ファイルおよびストリーム入出力](https://msdn.microsoft.com/library/k3352a4t)  
 [非同期ファイル I/O](https://msdn.microsoft.com/library/kztecsys)  
 [.NET Framework のファイル I/O とファイル システムで使用するクラス (Visual Basic)](../../../../visual-basic/developing-apps/programming/drives-directories-files/classes-used-in-net-framework-file-io-and-the-file-system.md)
