# FirstTime
library(tm)
library(tm.plugin.mail)
mbox <- MBoxSource(“/var/spool/mail/user”, encoding = “UTF8”)
sometimes it’s very useful to keep a text backup for each mail message.
convert_mbox_eml(mbox = “/var/spool/mail/user”, dir = “/home/user/my_mail_text”)
or getting Corpora alive right from mailbox
mail_messages <- VCorpus(MBoxSource(“/var/spool/mail/user”, encoding = “UTF8”), readerControl = list(reader = readMail))
some cleaning
mail_messages <- tm_map(mail_messages, removeCitation)
mail_messages <- tm_map(mail_messages, removeSignature)
take a peek at content
mail_messages[[1]]$meta$author
mail_messages[[1]]$meta$heading
mail_messages[[1]]$meta$header
