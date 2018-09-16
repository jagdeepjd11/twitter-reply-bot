# twitter-reply-bot
console.log('the bot is starting');

var Twit = require ('twit');

var config = require('./config');
var T = new Twit(config);

var query = "alot";

T.get('search/tweets',
    { q: query, count: 1, lang: "en" },
    function (_error, tweets) {
        var tweetList = tweets['statuses'];}
    
        for (var i = 0; i < tweetList.length; i++) {
            var id = { id: tweetList[i].id_str }
            if ('retweeted_status' in tweetList[i]) 
                continue;
            }
       
        
            var message = "Alot confused, a lot not understand feelings";
            var tweetId = tweetList[i].id_str

            try {
                T.post('statuses/update',
                    { "status": message, "in_reply_to_status_id": tweetId },
                    function (error, tweets, response) {
                        console.log("Tweet posted successfully!")
                    });
            }
            catch (err) {
                console.log(err);
        }
    });
