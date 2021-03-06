$Id: readme_ja.txt,v 1.2 2011/12/29 20:06:57 ohwada Exp $

=================================================
Version: 1.20
Date:   2011-12-29
Author: Kenichi OHWADA
URL:    https://linux.ohwada.jp/
Email:  webmaster@ohwada.jp
=================================================

このモジュールは、 XoopsHeadline モジュールと同等の機能です。

● 変更内容
1. PHP 5.3 対応
PHP 5.3.x で推奨されない機能 を修正した
https://www.php.net/manual/ja/migration53.deprecated.php
(1) new の返り値を参照で代入すること

2. MySQL 5.5 対応
(1) TYPE=MyISAM -> ENGINE=MyISAM
(2) BLOB/TEXT can't have a default value


=================================================
Version: 1.15
Date:   2008-01-18
=================================================

このモジュールは、 XoopsHeadline モジュールと同等の機能です。

変更内容
(1) ドイツ語を追加した


=================================================
Version: 1.14
Date:   2007-08-01
=================================================

このモジュールは、 XoopsHeadline モジュールと同等の機能です。

変更内容
(1) 日本語 UTF-8 版を追加した


=================================================
Version: 1.13
Date:   2007-06-09
=================================================

このモジュールは、 XoopsHeadline モジュールと同等の機能です。

変更内容
(1) RSSCモジュール (v0.60) の変更に合わせて、修正した
(2) Happy_linux モジュール v0.90 が必要です。


=================================================
Version: 1.12
Date:   2007-05-20
=================================================

このモジュールは、 XoopsHeadline モジュールと同等の機能です。

変更内容
(1) lastbuilddate がないときは、pubdate を表示する
(2) ペルシャ語ファイルを追加した (xoops persian 翻訳)


=================================================
Version: 1.11
Date:   2006-09-10
=================================================

このモジュールは、 XoopsHeadline モジュールと同等の機能です。

変更内容
(1) RSSCモジュールの変更に合わせて、修正した
(2) URL形式ではない guid を持つ RSS に対応した
(3) ヘッドラインの登録時に、RSSが解析出来ないときは、その旨を表示した


=================================================
Version: 1.10
Date:   2006-07-10
=================================================

このモジュールは、 XoopsHeadline モジュールと同等の機能です。

● モジュール概要
XoopsHeadline をベースに、
RSSフィードの管理機能を RSSCモジュールを利用するように変更したものです。
RSSCモジュールの連携機能のサンプルとして作成しました。

● XoopsHeadline との違い
変更は必要最低限に留めています。
XoopsHeadline にて使い勝手が悪いところはそのまま継承されています。

RSSCモジュールの連携機能を利用したことにより、
下記の点が改良されています。

(1) RSS Auto Discovery (自動検出) への対応
登録するWEBサイトが RSS Auto Discovery に対応している場合は、
「RDF/RSSファイルのURL」 と 「RSSエンコード」 を記入しなくとも、
自動的に設定されます。

登録するときに、RSS Auto Discovery を実行し、
検出された「RDF/RSSファイルのURL」が設定されます。
検出されないときは、その旨を表示します。
また、RSSC モジュールに 同じ「RDF/RSSファイルのURL」が存在するかを検査し、
存在すれは、すでにあるものを利用します。

(2) allow_url_fopen = off に対応した

● 要求事項
happy_linux モジュールとRSSセンター・モジュールが必要です。

● 課題
２つのモジュールを連携したことにより、
モジュール間に不整合が発生することがあります。

(1) RSSC にてリンクを削除した
RSSC 側にてリンクを削除しても、rssheadline 側は削除されません。
rssheadline 側では、リンクがあるのに、
RSSフィード が表示されないという不具合が発生します。

この不具合は、管理者が修正することで、解決します。
RSSC 側にて 削除したリンクを再度 登録してください。
rssheadline 側にて、登録したリンクのIDに変更してください。

(2) RSSC にて同じ「RDF/RSSファイルのURL」が複数存在する。
rssheadline 側にて間違った「RDF/RSSファイルのURL」のリンクを追加すると、
RSSC 側にも間違ったリンクが追加されます。
その後「RDF/RSSファイルのURL」を修正すると、
RSSC 側も修正されます。
修正した「RDF/RSSファイルのURL」が、
RSSC 側に存在していた場合に、
RSSC 側にて同じ「RDF/RSSファイルのURL」が複数存在することになります。

RSSC 側では、
リンクAを更新したときには、RSSフィードはリンクAに属するものとして追加され、
リンクBを更新したときには、RSSフィードはリンクBに属するものとして追加されます。
また同じRSSフィードは追加しないという仕組みになっています。
そのため、リンクAには、RSSフィード1,3,5が属して、
リンクBには、RSSフィード2,4,6が属するようになります。

rssheadline 側では、リンクAとリンクBのいずれに表示しても、
RSSフィード1,2,3,4,5,6が表示されるのが理想的な姿ですが、
現状では、リンクAではRSSフィード1,3,5のみが表示されるという不具合が発生します。

この不具合は、管理者が修正することで、解決します。
rssheadline 側 と RSSC 側の両方で、重複しているリンクを削除してください。
