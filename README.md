PGDMP     "    ,                 u            pb    9.3.5    9.3.5 /   o           0    0    ENCODING    ENCODING        SET client_encoding = 'UTF8';
                       false            p           0    0 
   STDSTRINGS 
   STDSTRINGS     (   SET standard_conforming_strings = 'on';
                       false            q           1262    19332    pb    DATABASE        CREATE DATABASE pb WITH TEMPLATE = template0 ENCODING = 'UTF8' LC_COLLATE = 'Indonesian_Indonesia.1252' LC_CTYPE = 'Indonesian_Indonesia.1252';
    DROP DATABASE pb;
             postgres    false                        2615    2200    public    SCHEMA        CREATE SCHEMA public;
    DROP SCHEMA public;
             postgres    false            r           0    0 
   SCHEMA public    COMMENT     6   COMMENT ON SCHEMA public IS 'standard public schema';
                  postgres    false    6            s           0    0    public    ACL     ¢   REVOKE ALL ON SCHEMA public FROM PUBLIC;
REVOKE ALL ON SCHEMA public FROM postgres;
GRANT ALL ON SCHEMA public TO postgres;
GRANT ALL ON SCHEMA public TO PUBLIC;
                  postgres    false    6            è            3079    11750    plpgsql 	   EXTENSION     ?   CREATE EXTENSION IF NOT EXISTS plpgsql WITH SCHEMA pg_catalog;
    DROP EXTENSION plpgsql;
                  false            t           0    0    EXTENSION plpgsql    COMMENT     @   COMMENT ON EXTENSION plpgsql IS 'PL/pgSQL procedural language';
                       false    232            ï            1255    19333    insert_account_activity()    FUNCTION     à   CREATE FUNCTION insert_account_activity() RETURNS trigger
    LANGUAGE plpgsql
    AS $$
            BEGIN
            INSERT INTO account_activity(account_id) VALUES (NEW.id);
            RETURN NEW;
            END$$;
 0   DROP FUNCTION public.insert_account_activity();
       public       postgres    false    232    6            ö            1255    19334    insert_player_stats()    FUNCTION     ×   CREATE FUNCTION insert_player_stats() RETURNS trigger
    LANGUAGE plpgsql
    AS $$
            BEGIN
            INSERT INTO player_stats(player_id) VALUES (NEW.id);
            RETURN NEW;
            END$$;
 ,   DROP FUNCTION public.insert_player_stats();
       public       postgres    false    232    6            ª            1259    19335    account_access    TABLE     \   CREATE TABLE account_access (
    accountid integer NOT NULL,
    level integer NOT NULL
);
 "   DROP TABLE public.account_access;
       public         postgres    false    6            u           0    0    TABLE account_access    COMMENT     9   COMMENT ON TABLE account_access IS 'Ã€Ã¤Ã¬Ã¨Ã­Ã‹Ã¨Ã±Ã²';
            public       postgres    false    170            v           0    0    COLUMN account_access.accountid    COMMENT     E   COMMENT ON COLUMN account_access.accountid IS 'ID Ã ÃªÃªÃ Ã³Ã­Ã²Ã ';
            public       postgres    false    170            w           0    0    COLUMN account_access.level    COMMENT     <   COMMENT ON COLUMN account_access.level IS 'Ã“Ã°Ã®Ã¢Ã¥Ã­Ã¼';
            public       postgres    false    170            «            1259    19338    account_activity    TABLE       CREATE TABLE account_activity (
    account_id bigint NOT NULL,
    last_active timestamp with time zone DEFAULT now() NOT NULL,
    last_ip character varying(15) DEFAULT '127.0.0.1'::character varying NOT NULL,
    total_active integer DEFAULT 0 NOT NULL
);
 $   DROP TABLE public.account_activity;
       public         postgres    false    6            x           0    0    TABLE account_activity    COMMENT     X   COMMENT ON TABLE account_activity IS 'Ã€ÃªÃ²Ã¨Ã¢Ã­Ã®Ã±Ã²Ã¼ Ã¯Ã®Ã«Ã¼Ã§Ã®Ã¢Ã Ã²Ã¥Ã«Ã¥Ã©';
            public       postgres    false    171            y           0    0 "   COLUMN account_activity.account_id    COMMENT     H   COMMENT ON COLUMN account_activity.account_id IS 'ID Ã ÃªÃªÃ Ã³Ã­Ã²Ã ';
            public       postgres    false    171            z           0    0 #   COLUMN account_activity.last_active    COMMENT     ]   COMMENT ON COLUMN account_activity.last_active IS 'ÃÃ®Ã±Ã«Ã¥Ã¤Ã­Ã¿Ã¿ Ã ÃªÃ²Ã¨Ã¢Ã­Ã®Ã±Ã²Ã¼';
            public       postgres    false    171            {           0    0    COLUMN account_activity.last_ip    COMMENT     G   COMMENT ON COLUMN account_activity.last_ip IS 'ÃÃ®Ã±Ã«Ã¥Ã¤Ã­Ã¨Ã© ip';
            public       postgres    false    171            |           0    0 $   COLUMN account_activity.total_active    COMMENT     g   COMMENT ON COLUMN account_activity.total_active IS 'Ã‚Ã±Ã¥Ã£Ã® Ã¢ Ã®Ã­Ã«Ã Ã©Ã­Ã¥ (Ã¢ Ã¬Ã¨Ã­Ã³Ã²Ã Ãµ)';
            public       postgres    false    171            ¬            1259    19344    account_banned    TABLE     !  CREATE TABLE account_banned (
    type character varying(25) NOT NULL,
    value character varying(25) NOT NULL,
    date_lock timestamp with time zone NOT NULL,
    date_unlock timestamp with time zone NOT NULL,
    owner_id bigint NOT NULL,
    reason character varying(150) NOT NULL
);
 "   DROP TABLE public.account_banned;
       public         postgres    false    6            }           0    0    TABLE account_banned    COMMENT     V   COMMENT ON TABLE account_banned IS 'Ã‡Ã Ã¡Ã«Ã®ÃªÃ¨Ã°Ã®Ã¢Ã Ã­Ã­Ã»Ã¥ Ã ÃªÃªÃ Ã³Ã­Ã²Ã»';
            public       postgres    false    172            ~           0    0    COLUMN account_banned.type    COMMENT     E   COMMENT ON COLUMN account_banned.type IS 'Ã’Ã¨Ã¯ Ã¡Ã Ã­Ã  (IP/MAC)';
            public       postgres    false    172                       0    0    COLUMN account_banned.value    COMMENT     c   COMMENT ON COLUMN account_banned.value IS 'Ã‡Ã­Ã Ã·Ã¥Ã­Ã¨Ã¥ Ã²Ã¨Ã¯Ã  (Ã‹Ã¨Ã¡Ã® ip, Ã«Ã¨Ã¡Ã® Mac)';
            public       postgres    false    172            €           0    0    COLUMN account_banned.date_lock    COMMENT     \   COMMENT ON COLUMN account_banned.date_lock IS 'Ã„Ã Ã²Ã  Ã­Ã Ã·Ã Ã«Ã  Ã¡Ã«Ã®ÃªÃ¨Ã°Ã®Ã¢ÃªÃ¨';
            public       postgres    false    172                       0    0 !   COLUMN account_banned.date_unlock    COMMENT     d   COMMENT ON COLUMN account_banned.date_unlock IS 'Ã„Ã Ã²Ã  Ã®ÃªÃ®Ã­Ã·Ã Ã­Ã¨Ã¿ Ã¡Ã«Ã®ÃªÃ¨Ã°Ã®Ã¢ÃªÃ¨';
            public       postgres    false    172            ‚           0    0    COLUMN account_banned.owner_id    COMMENT     P   COMMENT ON COLUMN account_banned.owner_id IS 'ÃŠÃ²Ã® Ã§Ã Ã¡Ã«Ã®ÃªÃ¨Ã°Ã®Ã¢Ã Ã«';
            public       postgres    false    172            ƒ           0    0    COLUMN account_banned.reason    COMMENT     R   COMMENT ON COLUMN account_banned.reason IS 'ÃÃ°Ã¨Ã·Ã¨Ã­Ã  Ã¡Ã«Ã®ÃªÃ¨Ã°Ã®Ã¢ÃªÃ¨';
            public       postgres    false    172            ­            1259    19347    account_bonuses    TABLE     ‘   CREATE TABLE account_bonuses (
    account_id bigint NOT NULL,
    bonus integer NOT NULL,
    bonus_expire timestamp with time zone NOT NULL
);
 #   DROP TABLE public.account_bonuses;
       public         postgres    false    6            „           0    0    TABLE account_bonuses    COMMENT     O   COMMENT ON TABLE account_bonuses IS 'ÃÃ®Ã­Ã³Ã±Ã» Ã¯Ã®Ã«Ã¼Ã§Ã®Ã¢Ã Ã²Ã¥Ã«Ã¥Ã©';
            public       postgres    false    173            …           0    0 !   COLUMN account_bonuses.account_id    COMMENT     G   COMMENT ON COLUMN account_bonuses.account_id IS 'ID Ã ÃªÃªÃ Ã³Ã­Ã²Ã ';
            public       postgres    false    173            †           0    0    COLUMN account_bonuses.bonus    COMMENT     B   COMMENT ON COLUMN account_bonuses.bonus IS 'Ã’Ã¨Ã¯ Ã¡Ã®Ã­Ã³Ã±Ã ';
            public       postgres    false    173            ‡           0    0 #   COLUMN account_bonuses.bonus_expire    COMMENT     F   COMMENT ON COLUMN account_bonuses.bonus_expire IS 'ÃˆÃ±Ã²Ã¥ÃªÃ Ã¥Ã²';
            public       postgres    false    173            ®            1259    19350    accounts_id_seq    SEQUENCE     q   CREATE SEQUENCE accounts_id_seq
    START WITH 8
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;
 &   DROP SEQUENCE public.accounts_id_seq;
       public       postgres    false    6            ¯            1259    19352    accounts    TABLE     g  CREATE TABLE accounts (
    id bigint DEFAULT nextval('accounts_id_seq'::regclass) NOT NULL,
    login character varying(50) NOT NULL,
    password character varying(100) NOT NULL,
    email character varying(100) NOT NULL,
    money integer DEFAULT 0 NOT NULL,
    active boolean DEFAULT true NOT NULL,
    mac character varying,
    ip character varying
);
    DROP TABLE public.accounts;
       public         postgres    false    174    6            ˆ           0    0    TABLE accounts    COMMENT     9   COMMENT ON TABLE accounts IS 'ÃÃ®Ã«Ã¼Ã§Ã®Ã¢Ã Ã²Ã¥Ã«Ã¨';
            public       postgres    false    175            ‰           0    0    COLUMN accounts.id    COMMENT     8   COMMENT ON COLUMN accounts.id IS 'ID Ã ÃªÃªÃ Ã³Ã­Ã²Ã ';
            public       postgres    false    175            Š           0    0    COLUMN accounts.login    COMMENT     2   COMMENT ON COLUMN accounts.login IS 'Ã‹Ã®Ã£Ã¨Ã­';
            public       postgres    false    175            ‹           0    0    COLUMN accounts.password    COMMENT     7   COMMENT ON COLUMN accounts.password IS 'ÃÃ Ã°Ã®Ã«Ã¼';
            public       postgres    false    175            Œ           0    0    COLUMN accounts.email    COMMENT     -   COMMENT ON COLUMN accounts.email IS 'Email';
            public       postgres    false    175                       0    0    COLUMN accounts.money    COMMENT     4   COMMENT ON COLUMN accounts.money IS 'Ã„Ã¥Ã­Ã¼Ã£Ã¨';
            public       postgres    false    175            Ž           0    0    COLUMN accounts.active    COMMENT     ?   COMMENT ON COLUMN accounts.active IS 'Ã€ÃªÃ²Ã¨Ã¢Ã¨Ã°Ã®Ã¢Ã Ã­';
            public       postgres    false    175            °            1259    19361    channels_id_seq    SEQUENCE     q   CREATE SEQUENCE channels_id_seq
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;
 &   DROP SEQUENCE public.channels_id_seq;
       public       postgres    false    6            ±            1259    19363    channels    TABLE     Ù   CREATE TABLE channels (
    id bigint DEFAULT nextval('channels_id_seq'::regclass) NOT NULL,
    gameserver_id bigint NOT NULL,
    type character varying(25) NOT NULL,
    announce character varying(150) NOT NULL
);
    DROP TABLE public.channels;
       public         postgres    false    176    6                       0    0    TABLE channels    COMMENT     <   COMMENT ON TABLE channels IS 'Ã‘Ã¯Ã¨Ã±Ã®Ãª ÃªÃ Ã­Ã Ã«Ã®Ã¢';
            public       postgres    false    177                       0    0    COLUMN channels.id    COMMENT     '   COMMENT ON COLUMN channels.id IS 'ID';
            public       postgres    false    177            ‘           0    0    COLUMN channels.gameserver_id    COMMENT     2   COMMENT ON COLUMN channels.gameserver_id IS 'ID';
            public       postgres    false    177            ’           0    0    COLUMN channels.type    COMMENT     :   COMMENT ON COLUMN channels.type IS 'Ã’Ã¨Ã¯ ÃªÃ Ã­Ã Ã«Ã ';
            public       postgres    false    177            “           0    0    COLUMN channels.announce    COMMENT     A   COMMENT ON COLUMN channels.announce IS 'AÃ­Ã®Ã­Ã± ÃªÃ Ã­Ã Ã«Ã ';
            public       postgres    false    177            ²            1259    19367    clans_id_seq    SEQUENCE     n   CREATE SEQUENCE clans_id_seq
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;
 #   DROP SEQUENCE public.clans_id_seq;
       public       postgres    false    6            ³            1259    19369    clans    TABLE     Ä  CREATE TABLE clans (
    id bigint DEFAULT nextval('clans_id_seq'::regclass) NOT NULL,
    name character varying(50) NOT NULL,
    rank integer NOT NULL,
    owner_id bigint NOT NULL,
    color integer NOT NULL,
    logo1 integer,
    logo2 integer,
    logo3 integer,
    logo4 integer,
    info character varying,
    notice character varying(255),
    create_date integer,
    players integer,
    max_players integer,
    exp integer DEFAULT 0
);
    DROP TABLE public.clans;
       public         postgres    false    178    6            ”           0    0    TABLE clans    COMMENT     (   COMMENT ON TABLE clans IS 'ÃŠÃ«Ã Ã­Ã»';
            public       postgres    false    179            •           0    0    COLUMN clans.id    COMMENT     /   COMMENT ON COLUMN clans.id IS 'ID ÃªÃ«Ã Ã­Ã ';
            public       postgres    false    179            –           0    0    COLUMN clans.name    COMMENT     ?   COMMENT ON COLUMN clans.name IS 'ÃÃ Ã§Ã¢Ã Ã­Ã¨Ã¥ ÃªÃ«Ã Ã­Ã ';
            public       postgres    false    179            —           0    0    COLUMN clans.rank    COMMENT     7   COMMENT ON COLUMN clans.rank IS 'ÃÃ Ã­Ã£ ÃªÃ«Ã Ã­Ã ';
            public       postgres    false    179            ˜           0    0    COLUMN clans.owner_id    COMMENT     N   COMMENT ON COLUMN clans.owner_id IS 'ÃˆÃ£Ã°Ã®Ãª Ã±Ã®Ã§Ã¤Ã Ã¢Ã¸Ã¨Ã© ÃªÃ«Ã Ã­';
            public       postgres    false    179            ™           0    0    COLUMN clans.color    COMMENT     I   COMMENT ON COLUMN clans.color IS 'Ã–Ã¢Ã¥Ã² Ã­Ã Ã§Ã¢Ã Ã­Ã¨Ã¿ ÃªÃ«Ã Ã­Ã ';
            public       postgres    false    179            š           0    0    COLUMN clans.logo1    COMMENT     -   COMMENT ON COLUMN clans.logo1 IS 'Ã‹Ã®Ã£Ã®';
            public       postgres    false    179            ›           0    0    COLUMN clans.logo2    COMMENT     -   COMMENT ON COLUMN clans.logo2 IS 'Ã‹Ã®Ã£Ã®';
            public       postgres    false    179            œ           0    0    COLUMN clans.logo3    COMMENT     -   COMMENT ON COLUMN clans.logo3 IS 'Ã‹Ã®Ã£Ã®';
            public       postgres    false    179                       0    0    COLUMN clans.logo4    COMMENT     -   COMMENT ON COLUMN clans.logo4 IS 'Ã‹Ã®Ã£Ã®';
            public       postgres    false    179            ´            1259    19377 
   contas_seq    SEQUENCE     l   CREATE SEQUENCE contas_seq
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;
 !   DROP SEQUENCE public.contas_seq;
       public       postgres    false    6            µ            1259    19379    contas    TABLE       CREATE TABLE contas (
    id bigint DEFAULT nextval('contas_seq'::regclass) NOT NULL,
    login character varying(255) DEFAULT ''::character varying NOT NULL,
    senha character varying(255) DEFAULT ''::character varying NOT NULL,
    status integer NOT NULL,
    ip character varying(32) DEFAULT ''::character varying NOT NULL,
    mac character varying(32) DEFAULT ''::character varying NOT NULL,
    online integer DEFAULT 0 NOT NULL,
    data character varying(255) DEFAULT ''::character varying NOT NULL
);
    DROP TABLE public.contas;
       public         postgres    false    180    6            ¶            1259    19392    event    TABLE     [  CREATE TABLE event (
    id integer NOT NULL,
    type integer NOT NULL,
    nome character varying DEFAULT ''::character varying NOT NULL,
    total integer NOT NULL,
    inicio character varying(255) DEFAULT ''::character varying NOT NULL,
    fim character varying(255) NOT NULL,
    mensagem character varying DEFAULT ''::character varying
);
    DROP TABLE public.event;
       public         postgres    false    6            ·            1259    19401 
   event_item    TABLE     ì   CREATE TABLE event_item (
    id integer NOT NULL,
    total integer NOT NULL,
    item_id integer NOT NULL,
    nome character varying DEFAULT ''::character varying,
    count integer NOT NULL,
    active integer DEFAULT 0 NOT NULL
);
    DROP TABLE public.event_item;
       public         postgres    false    6            ¸            1259    19409 
   event_show    TABLE     ¬   CREATE TABLE event_show (
    event integer NOT NULL,
    dia integer NOT NULL,
    total integer NOT NULL,
    item_id1 integer NOT NULL,
    item_id2 integer NOT NULL
);
    DROP TABLE public.event_show;
       public         postgres    false    6            ¹            1259    19412    gameservers_id_seq    SEQUENCE     t   CREATE SEQUENCE gameservers_id_seq
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;
 )   DROP SEQUENCE public.gameservers_id_seq;
       public       postgres    false    6            º            1259    19414    gameservers    TABLE        CREATE TABLE gameservers (
    id bigint DEFAULT nextval('gameservers_id_seq'::regclass) NOT NULL,
    password character varying(100) NOT NULL,
    type character varying(25) NOT NULL,
    max_players integer NOT NULL,
    CONSTRAINT check_max_player CHECK (((max_players % 10) = 0))
);
    DROP TABLE public.gameservers;
       public         postgres    false    185    6            ž           0    0    TABLE gameservers    COMMENT     A   COMMENT ON TABLE gameservers IS 'ÃˆÃ£Ã°Ã®Ã¢Ã»Ã¥ Ã±Ã¥Ã°Ã¢Ã¥Ã°Ã ';
            public       postgres    false    186            Ÿ           0    0    COLUMN gameservers.id    COMMENT     9   COMMENT ON COLUMN gameservers.id IS 'ID Ã±Ã¥Ã°Ã¢Ã¥Ã°Ã ';
            public       postgres    false    186                        0    0    COLUMN gameservers.password    COMMENT     @   COMMENT ON COLUMN gameservers.password IS 'ÃÃ Ã°Ã®Ã«Ã¼ (md5)';
            public       postgres    false    186            ¡           0    0    COLUMN gameservers.type    COMMENT     ?   COMMENT ON COLUMN gameservers.type IS 'Ã’Ã¨Ã¯ Ã±Ã¥Ã°Ã¢Ã¥Ã°Ã ';
            public       postgres    false    186            ¢           0    0    COLUMN gameservers.max_players    COMMENT     H   COMMENT ON COLUMN gameservers.max_players IS 'ÃŒÃ ÃªÃ± Ã¨Ã£Ã°Ã®ÃªÃ®Ã¢';
            public       postgres    false    186            »            1259    19419    goods    TABLE     Ø   CREATE TABLE goods (
    good_id integer NOT NULL,
    pricecredits integer NOT NULL,
    pricepoints integer NOT NULL,
    stocktype integer NOT NULL,
    title integer,
    quantity integer,
    item_id integer
);
    DROP TABLE public.goods;
       public         postgres    false    6            £           0    0    TABLE goods    COMMENT     *   COMMENT ON TABLE goods IS 'Ã’Ã®Ã¢Ã Ã°Ã»';
            public       postgres    false    187            ¤           0    0    COLUMN goods.good_id    COMMENT     6   COMMENT ON COLUMN goods.good_id IS 'id Ã²Ã®Ã¢Ã Ã°Ã ';
            public       postgres    false    187            ¥           0    0    COLUMN goods.pricecredits    COMMENT     H   COMMENT ON COLUMN goods.pricecredits IS 'Ã¶Ã¥Ã­Ã  Ã¢ ÃªÃ°Ã¥Ã¤Ã¨Ã²Ã Ãµ';
            public       postgres    false    187            ¦           0    0    COLUMN goods.pricepoints    COMMENT     A   COMMENT ON COLUMN goods.pricepoints IS 'Ã¶Ã¥Ã­Ã  Ã¢ Ã®Ã·ÃªÃ Ãµ';
            public       postgres    false    187            §           0    0    COLUMN goods.stocktype    COMMENT     /   COMMENT ON COLUMN goods.stocktype IS 'Ã’Ã¨Ã¯';
            public       postgres    false    187            ¼            1259    19422    hot_news    TABLE     i   CREATE TABLE hot_news (
    id integer,
    titolo character varying,
    contenuto character varying
);
    DROP TABLE public.hot_news;
       public         postgres    false    6            ½            1259    19428    ipsystem_id_seq    SEQUENCE     q   CREATE SEQUENCE ipsystem_id_seq
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;
 &   DROP SEQUENCE public.ipsystem_id_seq;
       public       postgres    false    6            ¾            1259    19430    ipsystem    TABLE     ã   CREATE TABLE ipsystem (
    id bigint DEFAULT nextval('ipsystem_id_seq'::regclass) NOT NULL,
    type character varying(5) NOT NULL,
    startpoint character varying(15) NOT NULL,
    endpoint character varying(15) NOT NULL
);
    DROP TABLE public.ipsystem;
       public         postgres    false    189    6            ¨           0    0    TABLE ipsystem    COMMENT     2   COMMENT ON TABLE ipsystem IS 'Ã‘Ã¨Ã±Ã²Ã¥Ã¬Ã  IP';
            public       postgres    false    190            ©           0    0    COLUMN ipsystem.id    COMMENT     )   COMMENT ON COLUMN ipsystem.id IS 'ÃˆÃ„';
            public       postgres    false    190            ª           0    0    COLUMN ipsystem.type    COMMENT     8   COMMENT ON COLUMN ipsystem.type IS 'Ã’Ã¨Ã¯ Ã°Ã Ã­Ã£Ã ';
            public       postgres    false    190            «           0    0    COLUMN ipsystem.startpoint    COMMENT     B   COMMENT ON COLUMN ipsystem.startpoint IS 'ÃÃ Ã·Ã Ã«Ã¼Ã­Ã»Ã© IP';
            public       postgres    false    190            ¬           0    0    COLUMN ipsystem.endpoint    COMMENT     P   COMMENT ON COLUMN ipsystem.endpoint IS 'ÃŠÃ®Ã­Ã¥Ã·Ã­Ã»Ã© IP Ã¨Ã«Ã¨ Ã¬Ã Ã±ÃªÃ ';
            public       postgres    false    190            ¿            1259    19434    items_id_seq    SEQUENCE     n   CREATE SEQUENCE items_id_seq
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;
 #   DROP SEQUENCE public.items_id_seq;
       public       postgres    false    6            À            1259    19436    items    TABLE     2  CREATE TABLE items (
    id bigint DEFAULT nextval('items_id_seq'::regclass) NOT NULL,
    type character varying(25) NOT NULL,
    slot_type character varying(25) NOT NULL,
    consume_type character varying(25) NOT NULL,
    consume_value integer,
    repair_credits integer,
    repair_points integer,
    repair_quantity integer,
    c_level integer,
    c_value integer,
    rb_id integer,
    CONSTRAINT check_consume_type CHECK ((((((consume_type)::text = 'DURABLE'::text) OR ((consume_type)::text = 'TEMPORARY'::text)) OR ((consume_type)::text = 'BAR'::text)) OR ((consume_type)::text = 'PERMANENT'::text))),
    CONSTRAINT check_consume_type_value CHECK (
CASE
    WHEN (((consume_type)::text = 'TEMPORARY'::text) OR ((consume_type)::text = 'DURABLE'::text)) THEN (consume_value IS NOT NULL)
    ELSE true
END),
    CONSTRAINT check_slot_type_by_type CHECK (
CASE
    WHEN ((type)::text = 'WEAPON'::text) THEN ((((((slot_type)::text = 'PRIM'::text) OR ((slot_type)::text = 'SUB'::text)) OR ((slot_type)::text = 'MELEE'::text)) OR ((slot_type)::text = 'THROWING'::text)) OR ((slot_type)::text = 'ITEM'::text))
    ELSE
    CASE
        WHEN ((type)::text = 'CHARACTER'::text) THEN ((((((slot_type)::text = 'CHAR_RED'::text) OR ((slot_type)::text = 'CHAR_BLUE'::text)) OR ((slot_type)::text = 'CHAR_HEAD'::text)) OR ((slot_type)::text = 'CHAR_ITEM'::text)) OR ((slot_type)::text = 'CHAR_DINO'::text))
        ELSE true
    END
END),
    CONSTRAINT check_type CHECK (((((type)::text = 'WEAPON'::text) OR ((type)::text = 'CHARACTER'::text)) OR ((type)::text = 'COUPON'::text)))
);
    DROP TABLE public.items;
       public         postgres    false    191    6            ­           0    0    TABLE items    COMMENT     .   COMMENT ON TABLE items IS 'ÃÃ°Ã¥Ã¤Ã¬Ã¥Ã²Ã»';
            public       postgres    false    192            ®           0    0    COLUMN items.id    COMMENT     $   COMMENT ON COLUMN items.id IS 'ID';
            public       postgres    false    192            ¯           0    0    COLUMN items.type    COMMENT     ;   COMMENT ON COLUMN items.type IS 'Ã’Ã¨Ã¯ Ã¯Ã°Ã¥Ã¤Ã¬Ã¥Ã²Ã ';
            public       postgres    false    192            °           0    0    COLUMN items.slot_type    COMMENT     k   COMMENT ON COLUMN items.slot_type IS 'Ã’Ã¨Ã¯ Ã±Ã«Ã®Ã²Ã®Ã¢ Ã¢ ÃªÃ®Ã²Ã®Ã°Ã»Ã¥ Ã¬Ã®Ã¦Ã¥Ã² Ã¡Ã»Ã²Ã¼ Ã®Ã¤Ã¥Ã²';
            public       postgres    false    192            ±           0    0    COLUMN items.consume_type    COMMENT     X   COMMENT ON COLUMN items.consume_type IS 'Ã†Ã¨Ã§Ã­Ã¥Ã­Ã­Ã»Ã© Ã¶Ã¨ÃªÃ« Ã¯Ã°Ã¥Ã¤Ã¬Ã¥Ã²Ã ';
            public       postgres    false    192            ²           0    0    COLUMN items.consume_value    COMMENT     Y   COMMENT ON COLUMN items.consume_value IS 'Ã†Ã¨Ã§Ã­Ã¥Ã­Ã­Ã»Ã© Ã¶Ã¨ÃªÃ« Ã¯Ã°Ã¥Ã¤Ã¬Ã¥Ã²Ã ';
            public       postgres    false    192            ³           0    0    COLUMN items.repair_credits    COMMENT     a   COMMENT ON COLUMN items.repair_credits IS 'Ã–Ã¥Ã­Ã  Ã¢ ÃªÃ°Ã¥Ã¤Ã¨Ã²Ã Ãµ Ã§Ã  Ã¯Ã®Ã·Ã¨Ã­ÃªÃ³ 1%';
            public       postgres    false    192            ´           0    0    COLUMN items.repair_points    COMMENT     Z   COMMENT ON COLUMN items.repair_points IS 'Ã–Ã¥Ã­Ã  Ã¢ Ã®Ã·ÃªÃ Ãµ Ã§Ã  Ã¯Ã®Ã·Ã¨Ã­ÃªÃ³ 1%';
            public       postgres    false    192            µ           0    0    COLUMN items.repair_quantity    COMMENT     k   COMMENT ON COLUMN items.repair_quantity IS 'ÃŒÃ ÃªÃ±Ã¨Ã¬Ã Ã«Ã¼Ã­Ã Ã¿ Ã¯Ã°Ã®Ã·Ã­Ã®Ã±Ã²Ã¼ Ã¯Ã°Ã¥Ã¤Ã¬Ã¥Ã²Ã ';
            public       postgres    false    192            Á            1259    19444    jogador    TABLE     S  CREATE TABLE jogador (
    id bigint NOT NULL,
    nick character varying(255) DEFAULT ''::character varying,
    rank integer DEFAULT 0 NOT NULL,
    gold integer DEFAULT 70000 NOT NULL,
    cash integer DEFAULT 25000 NOT NULL,
    exp integer DEFAULT 0 NOT NULL,
    color integer DEFAULT 0 NOT NULL,
    pc_cafe integer DEFAULT 0 NOT NULL,
    clan_id integer DEFAULT 0 NOT NULL,
    brooch integer DEFAULT 0 NOT NULL,
    insignia integer DEFAULT 0 NOT NULL,
    medal integer DEFAULT 0 NOT NULL,
    blue_order integer DEFAULT 0 NOT NULL,
    mission1 integer DEFAULT 1 NOT NULL,
    mission2 integer DEFAULT 0 NOT NULL,
    mission3 integer DEFAULT 0 NOT NULL,
    checks integer DEFAULT 0 NOT NULL,
    check_day integer DEFAULT 0 NOT NULL,
    minutos integer DEFAULT 0 NOT NULL,
    emblema integer DEFAULT 0 NOT NULL,
    cor_mira integer DEFAULT 0 NOT NULL,
    false_rank integer DEFAULT 55 NOT NULL,
    date integer DEFAULT 0 NOT NULL,
    access_level integer DEFAULT 0 NOT NULL,
    role integer DEFAULT 0 NOT NULL,
    false_nick character varying DEFAULT ''::character varying NOT NULL
);
    DROP TABLE public.jogador;
       public         postgres    false    6            Â            1259    19475    jogador_amigo_seq    SEQUENCE     s   CREATE SEQUENCE jogador_amigo_seq
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;
 (   DROP SEQUENCE public.jogador_amigo_seq;
       public       postgres    false    6            Ã            1259    19477 
   jogador_amigo    TABLE     ³   CREATE TABLE jogador_amigo (
    object bigint DEFAULT nextval('jogador_amigo_seq'::regclass) NOT NULL,
    player_id bigint NOT NULL,
    friend_id bigint,
    status integer
);
 !   DROP TABLE public.jogador_amigo;
       public         postgres    false    194    6            Ä            1259    19481    jogador_clan    TABLE     X  CREATE TABLE jogador_clan (
    id integer DEFAULT nextval('clans_id_seq'::regclass) NOT NULL,
    owner bigint NOT NULL,
    name character varying DEFAULT ''::character varying NOT NULL,
    notice character varying DEFAULT ''::character varying NOT NULL,
    info character varying DEFAULT ''::character varying NOT NULL,
    rank integer DEFAULT 0,
    logo1 integer DEFAULT 0,
    logo2 integer DEFAULT 0,
    logo3 integer DEFAULT 0,
    logo4 integer DEFAULT 0,
    color integer DEFAULT 0,
    partidas integer DEFAULT 0,
    vitorias integer DEFAULT 0,
    derrotas integer DEFAULT 0,
    autoridade integer DEFAULT 0,
    limite_rank integer DEFAULT 0,
    limite_idade integer DEFAULT 0,
    limite_idade2 integer DEFAULT 0,
    pontos integer DEFAULT 1000,
    vagas integer DEFAULT 50,
    exp integer DEFAULT 0,
    data integer DEFAULT 0
);
     DROP TABLE public.jogador_clan;
       public         postgres    false    178    6            Å            1259    19508    jogador_config    TABLE     Ð  CREATE TABLE jogador_config (
    player_id bigint NOT NULL,
    config integer NOT NULL,
    sangue integer NOT NULL,
    mira integer NOT NULL,
    mao integer NOT NULL,
    audio1 integer NOT NULL,
    audio2 integer NOT NULL,
    audio_enable integer NOT NULL,
    sensibilidade integer NOT NULL,
    visao integer NOT NULL,
    mouse_invertido integer NOT NULL,
    msgconvite integer NOT NULL,
    chatsusurro integer NOT NULL,
    macro integer NOT NULL
);
 "   DROP TABLE public.jogador_config;
       public         postgres    false    6            Æ            1259    19511    jogador_equipamento    TABLE       CREATE TABLE jogador_equipamento (
    player_id bigint NOT NULL,
    weapon_primary integer NOT NULL,
    weapon_secundary integer NOT NULL,
    weapon_melee integer NOT NULL,
    weapon_grenade integer NOT NULL,
    weapon_special integer NOT NULL,
    char_red integer NOT NULL,
    char_blue integer NOT NULL,
    char_head integer NOT NULL,
    char_beret integer NOT NULL,
    char_dino integer NOT NULL
);
 '   DROP TABLE public.jogador_equipamento;
       public         postgres    false    6            Ç            1259    19514    jogador_estatisticas    TABLE       CREATE TABLE jogador_estatisticas (
    player_id bigint NOT NULL,
    partidas integer NOT NULL,
    ganhou integer NOT NULL,
    perdeu integer NOT NULL,
    matou integer NOT NULL,
    morreu integer NOT NULL,
    headshots integer NOT NULL,
    kitou integer NOT NULL
);
 (   DROP TABLE public.jogador_estatisticas;
       public         postgres    false    6            È            1259    19517    jogador_inventario_seq    SEQUENCE     x   CREATE SEQUENCE jogador_inventario_seq
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;
 -   DROP SEQUENCE public.jogador_inventario_seq;
       public       postgres    false    6            É            1259    19519    jogador_inventario    TABLE     1  CREATE TABLE jogador_inventario (
    object bigint DEFAULT nextval('jogador_inventario_seq'::regclass) NOT NULL,
    player_id bigint NOT NULL,
    item_id integer NOT NULL,
    nome character varying(255) DEFAULT ''::character varying NOT NULL,
    count integer NOT NULL,
    equip integer NOT NULL
);
 &   DROP TABLE public.jogador_inventario;
       public         postgres    false    200    6            Ê            1259    19524    jogador_invite    TABLE     x   CREATE TABLE jogador_invite (
    clan_id integer NOT NULL,
    player_id bigint NOT NULL,
    date integer NOT NULL
);
 "   DROP TABLE public.jogador_invite;
       public         postgres    false    6            Ë            1259    19527    jogador_mensagem_seq    SEQUENCE     v   CREATE SEQUENCE jogador_mensagem_seq
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;
 +   DROP SEQUENCE public.jogador_mensagem_seq;
       public       postgres    false    6            Ì            1259    19529    jogador_mensagem    TABLE     ‡  CREATE TABLE jogador_mensagem (
    object bigint DEFAULT nextval('jogador_mensagem_seq'::regclass) NOT NULL,
    player_id bigint NOT NULL,
    recipient_name character varying DEFAULT ''::character varying NOT NULL,
    texto character varying DEFAULT ''::character varying,
    type integer NOT NULL,
    status integer NOT NULL,
    dias integer NOT NULL,
    "time" integer NOT NULL
);
 $   DROP TABLE public.jogador_mensagem;
       public         postgres    false    203    6            ¶           0    0    TABLE jogador_mensagem    COMMENT        COMMENT ON TABLE jogador_mensagem IS 'ÃƒÆ’Ã¢â‚¬Å¾ÃƒÆ’Ã‚Â°ÃƒÆ’Ã‚Â³ÃƒÆ’Ã‚Â§ÃƒÆ’Ã‚Â¼ÃƒÆ’Ã‚Â¿ ÃƒÆ’Ã‚Â¯ÃƒÆ’Ã‚Â«ÃƒÆ’Ã‚Â¥ÃƒÆ’Ã‚Â¥ÃƒÆ’Ã‚Â°ÃƒÆ’Ã‚Â ';
            public       postgres    false    204            Í            1259    19538    jogador_missoes    TABLE     h  CREATE TABLE jogador_missoes (
    player_id bigint DEFAULT 0 NOT NULL,
    mission1_1 integer DEFAULT 0 NOT NULL,
    mission1_2 integer DEFAULT 0 NOT NULL,
    mission1_3 integer DEFAULT 0 NOT NULL,
    mission1_4 integer DEFAULT 0 NOT NULL,
    mission1_5 integer DEFAULT 0 NOT NULL,
    mission1_6 integer DEFAULT 0 NOT NULL,
    mission1_7 integer DEFAULT 0 NOT NULL,
    mission1_8 integer DEFAULT 0 NOT NULL,
    mission1_9 integer DEFAULT 0 NOT NULL,
    mission1_10 integer DEFAULT 0 NOT NULL,
    mission1_11 integer DEFAULT 0 NOT NULL,
    mission1_12 integer DEFAULT 0 NOT NULL,
    mission1_13 integer DEFAULT 0 NOT NULL,
    mission1_14 integer DEFAULT 0 NOT NULL,
    mission1_15 integer DEFAULT 0 NOT NULL,
    mission1_16 integer DEFAULT 0 NOT NULL,
    mission1_17 integer DEFAULT 0 NOT NULL,
    mission1_18 integer DEFAULT 0 NOT NULL,
    mission1_19 integer DEFAULT 0 NOT NULL,
    mission1_20 integer DEFAULT 0 NOT NULL,
    mission1_21 integer DEFAULT 0 NOT NULL,
    mission1_22 integer DEFAULT 0 NOT NULL,
    mission1_23 integer DEFAULT 0 NOT NULL,
    mission1_24 integer DEFAULT 0 NOT NULL,
    mission1_25 integer DEFAULT 0 NOT NULL,
    mission1_26 integer DEFAULT 0 NOT NULL,
    mission1_27 integer DEFAULT 0 NOT NULL,
    mission1_28 integer DEFAULT 0 NOT NULL,
    mission1_29 integer DEFAULT 0 NOT NULL,
    mission1_30 integer DEFAULT 0 NOT NULL,
    mission1_31 integer DEFAULT 0 NOT NULL,
    mission1_32 integer DEFAULT 0 NOT NULL,
    mission1_33 integer DEFAULT 0 NOT NULL,
    mission1_34 integer DEFAULT 0 NOT NULL,
    mission1_35 integer DEFAULT 0 NOT NULL,
    mission1_36 integer DEFAULT 0 NOT NULL,
    mission1_37 integer DEFAULT 0 NOT NULL,
    mission1_38 integer DEFAULT 0 NOT NULL,
    mission1_39 integer DEFAULT 0 NOT NULL,
    mission1_40 integer DEFAULT 0 NOT NULL,
    mission2_1 integer DEFAULT 0 NOT NULL,
    mission2_2 integer DEFAULT 0 NOT NULL,
    mission2_3 integer DEFAULT 0 NOT NULL,
    mission2_4 integer DEFAULT 0 NOT NULL,
    mission2_5 integer DEFAULT 0 NOT NULL,
    mission2_6 integer DEFAULT 0 NOT NULL,
    mission2_7 integer DEFAULT 0 NOT NULL,
    mission2_8 integer DEFAULT 0 NOT NULL,
    mission2_9 integer DEFAULT 0 NOT NULL,
    mission2_10 integer DEFAULT 0 NOT NULL,
    mission2_11 integer DEFAULT 0 NOT NULL,
    mission2_12 integer DEFAULT 0 NOT NULL,
    mission2_13 integer DEFAULT 0 NOT NULL,
    mission2_14 integer DEFAULT 0 NOT NULL,
    mission2_15 integer DEFAULT 0 NOT NULL,
    mission2_16 integer DEFAULT 0 NOT NULL,
    mission2_17 integer DEFAULT 0 NOT NULL,
    mission2_18 integer DEFAULT 0 NOT NULL,
    mission2_19 integer DEFAULT 0 NOT NULL,
    mission2_20 integer DEFAULT 0 NOT NULL,
    mission2_21 integer DEFAULT 0 NOT NULL,
    mission2_22 integer DEFAULT 0 NOT NULL,
    mission2_23 integer DEFAULT 0 NOT NULL,
    mission2_24 integer DEFAULT 0 NOT NULL,
    mission2_25 integer DEFAULT 0 NOT NULL,
    mission2_26 integer DEFAULT 0 NOT NULL,
    mission2_27 integer DEFAULT 0 NOT NULL,
    mission2_28 integer DEFAULT 0 NOT NULL,
    mission2_29 integer DEFAULT 0 NOT NULL,
    mission2_30 integer DEFAULT 0 NOT NULL,
    mission2_31 integer DEFAULT 0 NOT NULL,
    mission2_32 integer DEFAULT 0 NOT NULL,
    mission2_33 integer DEFAULT 0 NOT NULL,
    mission2_34 integer DEFAULT 0 NOT NULL,
    mission2_35 integer DEFAULT 0 NOT NULL,
    mission2_36 integer DEFAULT 0 NOT NULL,
    mission2_37 integer DEFAULT 0 NOT NULL,
    mission2_38 integer DEFAULT 0 NOT NULL,
    mission2_39 integer DEFAULT 0 NOT NULL,
    mission2_40 integer DEFAULT 0 NOT NULL,
    mission3_1 integer DEFAULT 0 NOT NULL,
    mission3_2 integer DEFAULT 0 NOT NULL,
    mission3_3 integer DEFAULT 0 NOT NULL,
    mission3_4 integer DEFAULT 0 NOT NULL,
    mission3_5 integer DEFAULT 0 NOT NULL,
    mission3_6 integer DEFAULT 0 NOT NULL,
    mission3_7 integer DEFAULT 0 NOT NULL,
    mission3_8 integer DEFAULT 0 NOT NULL,
    mission3_9 integer DEFAULT 0 NOT NULL,
    mission3_10 integer DEFAULT 0 NOT NULL,
    mission3_11 integer DEFAULT 0 NOT NULL,
    mission3_12 integer DEFAULT 0 NOT NULL,
    mission3_13 integer DEFAULT 0 NOT NULL,
    mission3_14 integer DEFAULT 0 NOT NULL,
    mission3_15 integer DEFAULT 0 NOT NULL,
    mission3_16 integer DEFAULT 0 NOT NULL,
    mission3_17 integer DEFAULT 0 NOT NULL,
    mission3_18 integer DEFAULT 0 NOT NULL,
    mission3_19 integer DEFAULT 0 NOT NULL,
    mission3_20 integer DEFAULT 0 NOT NULL,
    mission3_21 integer DEFAULT 0 NOT NULL,
    mission3_22 integer DEFAULT 0 NOT NULL,
    mission3_23 integer DEFAULT 0 NOT NULL,
    mission3_24 integer DEFAULT 0 NOT NULL,
    mission3_25 integer DEFAULT 0 NOT NULL,
    mission3_26 integer DEFAULT 0 NOT NULL,
    mission3_27 integer DEFAULT 0 NOT NULL,
    mission3_28 integer DEFAULT 0 NOT NULL,
    mission3_29 integer DEFAULT 0 NOT NULL,
    mission3_30 integer DEFAULT 0 NOT NULL,
    mission3_31 integer DEFAULT 0 NOT NULL,
    mission3_32 integer DEFAULT 0 NOT NULL,
    mission3_33 integer DEFAULT 0 NOT NULL,
    mission3_34 integer DEFAULT 0 NOT NULL,
    mission3_35 integer DEFAULT 0 NOT NULL,
    mission3_36 integer DEFAULT 0 NOT NULL,
    mission3_37 integer DEFAULT 0 NOT NULL,
    mission3_38 integer DEFAULT 0 NOT NULL,
    mission3_39 integer DEFAULT 0 NOT NULL,
    mission3_40 integer DEFAULT 0 NOT NULL,
    card1 integer DEFAULT 0 NOT NULL,
    card2 integer DEFAULT 0 NOT NULL,
    card3 integer DEFAULT 0 NOT NULL,
    active integer DEFAULT 0 NOT NULL
);
 #   DROP TABLE public.jogador_missoes;
       public         postgres    false    6            Î            1259    19666    jogador_teclado    TABLE     å  CREATE TABLE jogador_teclado (
    player_id bigint NOT NULL,
    k_esquerda integer DEFAULT 10,
    k_direita integer DEFAULT 13,
    k_frente integer DEFAULT 32,
    k_atras integer DEFAULT 28,
    k_pular integer DEFAULT 44,
    k_andar integer DEFAULT 40,
    k_agachar integer DEFAULT 38,
    k_o_atr integer DEFAULT 15,
    k_atirar integer DEFAULT 1,
    k_scope integer DEFAULT 2,
    k_recarregar integer DEFAULT 27,
    k_trc_arm integer DEFAULT 29,
    k_arm_qq integer DEFAULT 26,
    k_arm_ant integer DEFAULT 16,
    k_arm_pos integer DEFAULT 32,
    k_jog_arm integer DEFAULT 16,
    k_placar integer DEFAULT 55,
    k_mapa integer DEFAULT 22,
    k_mapa_pos integer DEFAULT 92,
    k_mapa_ant integer DEFAULT 91,
    k_chat integer DEFAULT 37,
    k_chat_g integer DEFAULT 64,
    k_chat_t integer DEFAULT 65,
    k_chat_hz integer DEFAULT 21,
    k_chat_v integer DEFAULT 31,
    k_chat_c integer DEFAULT 66,
    k_rad_t integer DEFAULT 35,
    k_rad_p integer DEFAULT 33,
    k_rad_i integer DEFAULT 12,
    k_bomb_d integer DEFAULT 14,
    k_sen_pos integer DEFAULT 49,
    k_sen_ant integer DEFAULT 50,
    k_print integer DEFAULT 70,
    k_mira_x integer DEFAULT 11,
    k_gravar integer DEFAULT 58,
    k_valor1 integer DEFAULT 57,
    k_valor2 integer DEFAULT 248,
    k_valor3 integer DEFAULT 16,
    k_valor4 integer DEFAULT 0,
    k_macro_e integer DEFAULT 69,
    armas1 integer DEFAULT 1,
    armas2 integer DEFAULT 2,
    armas3 integer DEFAULT 3,
    armas4 integer DEFAULT 4,
    armas5 integer DEFAULT 5,
    armas6 integer DEFAULT 6,
    macro1 character varying DEFAULT ''::character varying,
    macro2 character varying DEFAULT ''::character varying,
    macro3 character varying DEFAULT ''::character varying,
    macro4 character varying DEFAULT ''::character varying,
    macro5 character varying DEFAULT ''::character varying,
    macrolength1 integer DEFAULT 255,
    macrolength2 integer DEFAULT 255,
    macrolength3 integer DEFAULT 255,
    macrolength4 integer DEFAULT 255
);
 #   DROP TABLE public.jogador_teclado;
       public         postgres    false    6            Ï            1259    19727    jogador_teclado2    TABLE     ì  CREATE TABLE jogador_teclado2 (
    player_id bigint NOT NULL,
    v_1 integer DEFAULT 0,
    v_2 integer DEFAULT 0,
    v_3 integer DEFAULT 0,
    v_4 integer DEFAULT 0,
    v_5 integer DEFAULT 0,
    v_6 integer DEFAULT 0,
    v_7 integer DEFAULT 0,
    v_8 integer DEFAULT 0,
    v_9 integer DEFAULT 1,
    v_10 integer DEFAULT 1,
    v_11 integer DEFAULT 0,
    v_12 integer DEFAULT 0,
    v_13 integer DEFAULT 0,
    v_14 integer DEFAULT 0,
    v_15 integer DEFAULT 0,
    v_16 integer DEFAULT 0,
    v_17 integer DEFAULT 0,
    v_18 integer DEFAULT 0,
    v_19 integer DEFAULT 0,
    v_20 integer DEFAULT 1,
    v_21 integer DEFAULT 1,
    v_22 integer DEFAULT 0,
    v_23 integer DEFAULT 0,
    v_24 integer DEFAULT 0,
    v_25 integer DEFAULT 0,
    v_26 integer DEFAULT 0,
    v_27 integer DEFAULT 0,
    v_28 integer DEFAULT 0,
    v_29 integer DEFAULT 0,
    v_30 integer DEFAULT 0,
    v_31 integer DEFAULT 0,
    v_32 integer DEFAULT 0,
    v_33 integer DEFAULT 0,
    v_34 integer DEFAULT 0,
    v_35 integer DEFAULT 0,
    v_36 integer DEFAULT 0,
    v_37 integer DEFAULT 0,
    v_38 integer DEFAULT 0,
    v_39 integer DEFAULT 0,
    v_40 integer DEFAULT 0,
    v_41 integer DEFAULT 0,
    v_42 integer DEFAULT 0,
    v_43 integer DEFAULT 0
);
 $   DROP TABLE public.jogador_teclado2;
       public         postgres    false    6            Ð            1259    19773    jogador_titulos    TABLE     s  CREATE TABLE jogador_titulos (
    player_id bigint NOT NULL,
    slot integer NOT NULL,
    equip1 integer NOT NULL,
    equip2 integer NOT NULL,
    equip3 integer NOT NULL,
    pos1 integer NOT NULL,
    pos2 integer NOT NULL,
    pos3 integer NOT NULL,
    pos4 integer NOT NULL,
    pos5 integer NOT NULL,
    pos6 integer NOT NULL,
    title1 integer NOT NULL,
    title2 integer NOT NULL,
    title3 integer NOT NULL,
    title4 integer NOT NULL,
    title5 integer NOT NULL,
    title6 integer NOT NULL,
    title7 integer NOT NULL,
    title8 integer NOT NULL,
    title9 integer NOT NULL,
    title10 integer NOT NULL,
    title11 integer NOT NULL,
    title12 integer NOT NULL,
    title13 integer NOT NULL,
    title14 integer NOT NULL,
    title15 integer NOT NULL,
    title16 integer NOT NULL,
    title17 integer NOT NULL,
    title18 integer NOT NULL,
    title19 integer NOT NULL,
    title20 integer NOT NULL,
    title21 integer NOT NULL,
    title22 integer NOT NULL,
    title23 integer NOT NULL,
    title24 integer NOT NULL,
    title25 integer NOT NULL,
    title26 integer NOT NULL,
    title27 integer NOT NULL,
    title28 integer NOT NULL,
    title29 integer NOT NULL,
    title30 integer NOT NULL,
    title31 integer NOT NULL,
    title32 integer NOT NULL,
    title33 integer NOT NULL,
    title34 integer NOT NULL,
    title35 integer NOT NULL,
    title36 integer NOT NULL,
    title37 integer NOT NULL,
    title38 integer NOT NULL,
    title39 integer NOT NULL,
    title40 integer NOT NULL,
    title41 integer NOT NULL,
    title42 integer NOT NULL,
    title43 integer NOT NULL,
    title44 integer NOT NULL
);
 #   DROP TABLE public.jogador_titulos;
       public         postgres    false    6            Ñ            1259    19776    levelup    TABLE     º   CREATE TABLE levelup (
    rank integer NOT NULL,
    "needExp" integer NOT NULL,
    "allExp" integer NOT NULL,
    "rewardGP" integer NOT NULL,
    "rewardItems" integer[] NOT NULL
);
    DROP TABLE public.levelup;
       public         postgres    false    6            ·           0    0 
   TABLE levelup    COMMENT     !   COMMENT ON TABLE levelup IS 'G';
            public       postgres    false    209            ¸           0    0    COLUMN levelup.rank    COMMENT     .   COMMENT ON COLUMN levelup.rank IS 'ÃÃ Ã­Ã£';
            public       postgres    false    209            ¹           0    0    COLUMN levelup."needExp"    COMMENT     }   COMMENT ON COLUMN levelup."needExp" IS 'Ã‘ÃªÃ®Ã«Ã¼ÃªÃ® Ã­Ã³Ã¦Ã­Ã® Ã­Ã Ã¡Ã°Ã Ã²Ã¼ Ã®Ã¯Ã»Ã²Ã  Ã¤Ã® Ã±Ã«Ã¥Ã¤Ã³Ã¹Ã¥Ã£Ã® Ã€ÃÃ€';
            public       postgres    false    209            º           0    0    COLUMN levelup."allExp"    COMMENT     d   COMMENT ON COLUMN levelup."allExp" IS 'Ã‘ÃªÃ®Ã«Ã¼ÃªÃ® Ã¢Ã±Ã¥Ã£Ã® Ã®Ã¯Ã»Ã²Ã  Ã¤Ã®Ã«Ã¦Ã­Ã® Ã¡Ã»Ã²Ã¼';
            public       postgres    false    209            »           0    0    COLUMN levelup."rewardGP"    COMMENT     Z   COMMENT ON COLUMN levelup."rewardGP" IS 'Ã‘ÃªÃ®Ã«Ã¼ÃªÃ® Ã¤Ã¥Ã­Ã¥Ã£ Ã§Ã  Ã€Ã Ã¤Ã Ã¤Ã³Ã²';
            public       postgres    false    209            ¼           0    0    COLUMN levelup."rewardItems"    COMMENT     C   COMMENT ON COLUMN levelup."rewardItems" IS 'ÃˆÃ²Ã¥Ã¬Ã» Ã§Ã  Ã€Ã';
            public       postgres    false    209            Ò            1259    19782    missions    TABLE     g  CREATE TABLE missions (
    owner_id bigint DEFAULT 0 NOT NULL,
    mission1_1 integer DEFAULT 0 NOT NULL,
    mission1_2 integer DEFAULT 0 NOT NULL,
    mission1_3 integer DEFAULT 0 NOT NULL,
    mission1_4 integer DEFAULT 0 NOT NULL,
    mission1_5 integer DEFAULT 0 NOT NULL,
    mission1_6 integer DEFAULT 0 NOT NULL,
    mission1_7 integer DEFAULT 0 NOT NULL,
    mission1_8 integer DEFAULT 0 NOT NULL,
    mission1_9 integer DEFAULT 0 NOT NULL,
    mission1_10 integer DEFAULT 0 NOT NULL,
    mission1_11 integer DEFAULT 0 NOT NULL,
    mission1_12 integer DEFAULT 0 NOT NULL,
    mission1_13 integer DEFAULT 0 NOT NULL,
    mission1_14 integer DEFAULT 0 NOT NULL,
    mission1_15 integer DEFAULT 0 NOT NULL,
    mission1_16 integer DEFAULT 0 NOT NULL,
    mission1_17 integer DEFAULT 0 NOT NULL,
    mission1_18 integer DEFAULT 0 NOT NULL,
    mission1_19 integer DEFAULT 0 NOT NULL,
    mission1_20 integer DEFAULT 0 NOT NULL,
    mission1_21 integer DEFAULT 0 NOT NULL,
    mission1_22 integer DEFAULT 0 NOT NULL,
    mission1_23 integer DEFAULT 0 NOT NULL,
    mission1_24 integer DEFAULT 0 NOT NULL,
    mission1_25 integer DEFAULT 0 NOT NULL,
    mission1_26 integer DEFAULT 0 NOT NULL,
    mission1_27 integer DEFAULT 0 NOT NULL,
    mission1_28 integer DEFAULT 0 NOT NULL,
    mission1_29 integer DEFAULT 0 NOT NULL,
    mission1_30 integer DEFAULT 0 NOT NULL,
    mission1_31 integer DEFAULT 0 NOT NULL,
    mission1_32 integer DEFAULT 0 NOT NULL,
    mission1_33 integer DEFAULT 0 NOT NULL,
    mission1_34 integer DEFAULT 0 NOT NULL,
    mission1_35 integer DEFAULT 0 NOT NULL,
    mission1_36 integer DEFAULT 0 NOT NULL,
    mission1_37 integer DEFAULT 0 NOT NULL,
    mission1_38 integer DEFAULT 0 NOT NULL,
    mission1_39 integer DEFAULT 0 NOT NULL,
    mission1_40 integer DEFAULT 0 NOT NULL,
    activemission integer DEFAULT 0 NOT NULL,
    mission2_1 integer DEFAULT 0 NOT NULL,
    mission2_2 integer DEFAULT 0 NOT NULL,
    mission2_3 integer DEFAULT 0 NOT NULL,
    mission2_4 integer DEFAULT 0 NOT NULL,
    mission2_5 integer DEFAULT 0 NOT NULL,
    mission2_6 integer DEFAULT 0 NOT NULL,
    mission2_7 integer DEFAULT 0 NOT NULL,
    mission2_8 integer DEFAULT 0 NOT NULL,
    mission2_9 integer DEFAULT 0 NOT NULL,
    mission2_10 integer DEFAULT 0 NOT NULL,
    mission2_11 integer DEFAULT 0 NOT NULL,
    mission2_12 integer DEFAULT 0 NOT NULL,
    mission2_13 integer DEFAULT 0 NOT NULL,
    mission2_14 integer DEFAULT 0 NOT NULL,
    mission2_15 integer DEFAULT 0 NOT NULL,
    mission2_16 integer DEFAULT 0 NOT NULL,
    mission2_17 integer DEFAULT 0 NOT NULL,
    mission2_18 integer DEFAULT 0 NOT NULL,
    mission2_19 integer DEFAULT 0 NOT NULL,
    mission2_20 integer DEFAULT 0 NOT NULL,
    mission2_21 integer DEFAULT 0 NOT NULL,
    mission2_22 integer DEFAULT 0 NOT NULL,
    mission2_23 integer DEFAULT 0 NOT NULL,
    mission2_24 integer DEFAULT 0 NOT NULL,
    mission2_25 integer DEFAULT 0 NOT NULL,
    mission2_26 integer DEFAULT 0 NOT NULL,
    mission2_27 integer DEFAULT 0 NOT NULL,
    mission2_28 integer DEFAULT 0 NOT NULL,
    mission2_29 integer DEFAULT 0 NOT NULL,
    mission2_30 integer DEFAULT 0 NOT NULL,
    mission2_31 integer DEFAULT 0 NOT NULL,
    mission2_32 integer DEFAULT 0 NOT NULL,
    mission2_33 integer DEFAULT 0 NOT NULL,
    mission2_34 integer DEFAULT 0 NOT NULL,
    mission2_35 integer DEFAULT 0 NOT NULL,
    mission2_36 integer DEFAULT 0 NOT NULL,
    mission2_37 integer DEFAULT 0 NOT NULL,
    mission2_38 integer DEFAULT 0 NOT NULL,
    mission2_39 integer DEFAULT 0 NOT NULL,
    mission2_40 integer DEFAULT 0 NOT NULL,
    mission3_1 integer DEFAULT 0 NOT NULL,
    mission3_2 integer DEFAULT 0 NOT NULL,
    mission3_3 integer DEFAULT 0 NOT NULL,
    mission3_4 integer DEFAULT 0 NOT NULL,
    mission3_5 integer DEFAULT 0 NOT NULL,
    mission3_6 integer DEFAULT 0 NOT NULL,
    mission3_7 integer DEFAULT 0 NOT NULL,
    mission3_8 integer DEFAULT 0 NOT NULL,
    mission3_9 integer DEFAULT 0 NOT NULL,
    mission3_10 integer DEFAULT 0 NOT NULL,
    mission3_11 integer DEFAULT 0 NOT NULL,
    mission3_12 integer DEFAULT 0 NOT NULL,
    mission3_13 integer DEFAULT 0 NOT NULL,
    mission3_14 integer DEFAULT 0 NOT NULL,
    mission3_15 integer DEFAULT 0 NOT NULL,
    mission3_16 integer DEFAULT 0 NOT NULL,
    mission3_17 integer DEFAULT 0 NOT NULL,
    mission3_18 integer DEFAULT 0 NOT NULL,
    mission3_19 integer DEFAULT 0 NOT NULL,
    mission3_20 integer DEFAULT 0 NOT NULL,
    mission3_21 integer DEFAULT 0 NOT NULL,
    mission3_22 integer DEFAULT 0 NOT NULL,
    mission3_23 integer DEFAULT 0 NOT NULL,
    mission3_24 integer DEFAULT 0 NOT NULL,
    mission3_25 integer DEFAULT 0 NOT NULL,
    mission3_26 integer DEFAULT 0 NOT NULL,
    mission3_27 integer DEFAULT 0 NOT NULL,
    mission3_28 integer DEFAULT 0 NOT NULL,
    mission3_29 integer DEFAULT 0 NOT NULL,
    mission3_30 integer DEFAULT 0 NOT NULL,
    mission3_31 integer DEFAULT 0 NOT NULL,
    mission3_32 integer DEFAULT 0 NOT NULL,
    mission3_33 integer DEFAULT 0 NOT NULL,
    mission3_34 integer DEFAULT 0 NOT NULL,
    mission3_35 integer DEFAULT 0 NOT NULL,
    mission3_36 integer DEFAULT 0 NOT NULL,
    mission3_37 integer DEFAULT 0 NOT NULL,
    mission3_38 integer DEFAULT 0 NOT NULL,
    mission3_39 integer DEFAULT 0 NOT NULL,
    mission3_40 integer DEFAULT 0 NOT NULL,
    card1 integer DEFAULT 0 NOT NULL,
    card2 integer DEFAULT 0 NOT NULL,
    card3 integer DEFAULT 0 NOT NULL
);
    DROP TABLE public.missions;
       public         postgres    false    6            Ó            1259    19910    news    TABLE     Ÿ   CREATE TABLE news (
    id integer,
    titolo character varying,
    data character varying,
    autore character varying,
    contenuto character varying
);
    DROP TABLE public.news;
       public         postgres    false    6            Ô            1259    19916    player_bonus    TABLE        CREATE TABLE player_bonus (
    exp integer NOT NULL,
    gold integer NOT NULL,
    inicio character varying(255) DEFAULT ''::character varying NOT NULL,
    fim character varying(255) DEFAULT ''::character varying NOT NULL,
    ativo integer NOT NULL
);
     DROP TABLE public.player_bonus;
       public         postgres    false    6            Õ            1259    19924    player_clan    TABLE     t   CREATE TABLE player_clan (
    clan_id bigint NOT NULL,
    player_id bigint NOT NULL,
    rank integer NOT NULL
);
    DROP TABLE public.player_clan;
       public         postgres    false    6            ½           0    0    TABLE player_clan    COMMENT     O   COMMENT ON TABLE player_clan IS 'ÃÃ°Ã¨Ã¢Ã¿Ã§ÃªÃ  Ã¨Ã£Ã°Ã®ÃªÃ  Ãª ÃªÃ«Ã Ã­Ã³';
            public       postgres    false    213            ¾           0    0    COLUMN player_clan.clan_id    COMMENT     B   COMMENT ON COLUMN player_clan.clan_id IS 'ÃŠÃ«Ã Ã­ Ã¨Ã£Ã°Ã®ÃªÃ ';
            public       postgres    false    213            ¿           0    0    COLUMN player_clan.player_id    COMMENT     9   COMMENT ON COLUMN player_clan.player_id IS 'ÃˆÃ£Ã°Ã®Ãª';
            public       postgres    false    213            À           0    0    COLUMN player_clan.rank    COMMENT     ?   COMMENT ON COLUMN player_clan.rank IS 'ÃÃ Ã­Ã£ Ã¨Ã£Ã°Ã®ÃªÃ ';
            public       postgres    false    213            Ö            1259    19927 
   player_config    TABLE     ç   CREATE TABLE player_config (
    playerid bigint,
    mira integer,
    audio integer,
    audio1 integer,
    audio2 integer,
    vision integer,
    sensibility integer,
    mao integer,
    sangue integer,
    config integer
);
 !   DROP TABLE public.player_config;
       public         postgres    false    6            ×            1259    19930    player_eqipment_id_seq    SEQUENCE     z   CREATE SEQUENCE player_eqipment_id_seq
    START WITH 375
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;
 -   DROP SEQUENCE public.player_eqipment_id_seq;
       public       postgres    false    6            Ø            1259    19932    player_eqipment    TABLE       CREATE TABLE player_eqipment (
    id bigint DEFAULT nextval('player_eqipment_id_seq'::regclass) NOT NULL,
    player_id bigint NOT NULL,
    item_id bigint NOT NULL,
    count integer NOT NULL,
    loc character varying(25) NOT NULL,
    consume_lost integer,
    status integer
);
 #   DROP TABLE public.player_eqipment;
       public         postgres    false    215    6            Á           0    0    TABLE player_eqipment    COMMENT     E   COMMENT ON TABLE player_eqipment IS 'ÃÃ°Ã¥Ã¤Ã¬Ã¥Ã²Ã» Ã¨Ã£Ã°Ã®ÃªÃ ';
            public       postgres    false    216            Â           0    0    COLUMN player_eqipment.id    COMMENT     T   COMMENT ON COLUMN player_eqipment.id IS 'Ã“Ã­Ã¨ÃªÃ Ã«Ã¼Ã­Ã»Ã© ID Ã¯Ã°Ã¥Ã¤Ã¬Ã¥Ã²Ã ';
            public       postgres    false    216            Ã           0    0     COLUMN player_eqipment.player_id    COMMENT     B   COMMENT ON COLUMN player_eqipment.player_id IS 'id Ã¨Ã£Ã°Ã®ÃªÃ ';
            public       postgres    false    216            Ä           0    0    COLUMN player_eqipment.item_id    COMMENT     D   COMMENT ON COLUMN player_eqipment.item_id IS 'id Ã¯Ã°Ã¥Ã¤Ã¬Ã¥Ã²Ã ';
            public       postgres    false    216            Å           0    0    COLUMN player_eqipment.count    COMMENT     M   COMMENT ON COLUMN player_eqipment.count IS 'ÃŠÃ®Ã«-Ã¢Ã® Ã¯Ã°Ã¥Ã¤Ã¬Ã¥Ã²Ã®Ã¢';
            public       postgres    false    216            Æ           0    0    COLUMN player_eqipment.loc    COMMENT     F   COMMENT ON COLUMN player_eqipment.loc IS 'Ã£Ã¤Ã¥ Ã­Ã ÃµÃ®Ã¤Ã¨Ã²Ã±Ã¿';
            public       postgres    false    216            Ç           0    0 #   COLUMN player_eqipment.consume_lost    COMMENT     `   COMMENT ON COLUMN player_eqipment.consume_lost IS 'Ã„Ã Ã²Ã  Ã³Ã¤Ã Ã«Ã¥Ã­Ã¨Ã¿ Ã¯Ã°Ã¥Ã¤Ã¬Ã¥Ã²Ã ';
            public       postgres    false    216            Ù            1259    19936 $   player_friends_player_account_id_seq    SEQUENCE     †   CREATE SEQUENCE player_friends_player_account_id_seq
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;
 ;   DROP SEQUENCE public.player_friends_player_account_id_seq;
       public       postgres    false    6            Ú            1259    19938    player_friends    TABLE     ¬   CREATE TABLE player_friends (
    player_id bigint DEFAULT nextval('player_friends_player_account_id_seq'::regclass) NOT NULL,
    friend_id integer,
    status integer
);
 "   DROP TABLE public.player_friends;
       public         postgres    false    217    6            È           0    0    TABLE player_friends    COMMENT     @   COMMENT ON TABLE player_friends IS 'Ã„Ã°Ã³Ã§Ã¼Ã¿ Ã¯Ã«Ã¥Ã¥Ã°Ã ';
            public       postgres    false    218            É           0    0    COLUMN player_friends.player_id    COMMENT     A   COMMENT ON COLUMN player_friends.player_id IS 'ID Ã¯Ã«Ã¥Ã¥Ã°Ã ';
            public       postgres    false    218            Ê           0    0    COLUMN player_friends.friend_id    COMMENT     ?   COMMENT ON COLUMN player_friends.friend_id IS 'ID Ã¤Ã°Ã³Ã£Ã ';
            public       postgres    false    218            Û            1259    19942    player_message_seq    SEQUENCE     u   CREATE SEQUENCE player_message_seq
    START WITH 33
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;
 )   DROP SEQUENCE public.player_message_seq;
       public       postgres    false    6            Ü            1259    19944    player_missions    TABLE     n  CREATE TABLE player_missions (
    owner_id bigint DEFAULT 0 NOT NULL,
    mission1_1 integer DEFAULT 0 NOT NULL,
    mission1_2 integer DEFAULT 0 NOT NULL,
    mission1_3 integer DEFAULT 0 NOT NULL,
    mission1_4 integer DEFAULT 0 NOT NULL,
    mission1_5 integer DEFAULT 0 NOT NULL,
    mission1_6 integer DEFAULT 0 NOT NULL,
    mission1_7 integer DEFAULT 0 NOT NULL,
    mission1_8 integer DEFAULT 0 NOT NULL,
    mission1_9 integer DEFAULT 0 NOT NULL,
    mission1_10 integer DEFAULT 0 NOT NULL,
    mission1_11 integer DEFAULT 0 NOT NULL,
    mission1_12 integer DEFAULT 0 NOT NULL,
    mission1_13 integer DEFAULT 0 NOT NULL,
    mission1_14 integer DEFAULT 0 NOT NULL,
    mission1_15 integer DEFAULT 0 NOT NULL,
    mission1_16 integer DEFAULT 0 NOT NULL,
    mission1_17 integer DEFAULT 0 NOT NULL,
    mission1_18 integer DEFAULT 0 NOT NULL,
    mission1_19 integer DEFAULT 0 NOT NULL,
    mission1_20 integer DEFAULT 0 NOT NULL,
    mission1_21 integer DEFAULT 0 NOT NULL,
    mission1_22 integer DEFAULT 0 NOT NULL,
    mission1_23 integer DEFAULT 0 NOT NULL,
    mission1_24 integer DEFAULT 0 NOT NULL,
    mission1_25 integer DEFAULT 0 NOT NULL,
    mission1_26 integer DEFAULT 0 NOT NULL,
    mission1_27 integer DEFAULT 0 NOT NULL,
    mission1_28 integer DEFAULT 0 NOT NULL,
    mission1_29 integer DEFAULT 0 NOT NULL,
    mission1_30 integer DEFAULT 0 NOT NULL,
    mission1_31 integer DEFAULT 0 NOT NULL,
    mission1_32 integer DEFAULT 0 NOT NULL,
    mission1_33 integer DEFAULT 0 NOT NULL,
    mission1_34 integer DEFAULT 0 NOT NULL,
    mission1_35 integer DEFAULT 0 NOT NULL,
    mission1_36 integer DEFAULT 0 NOT NULL,
    mission1_37 integer DEFAULT 0 NOT NULL,
    mission1_38 integer DEFAULT 0 NOT NULL,
    mission1_39 integer DEFAULT 0 NOT NULL,
    mission1_40 integer DEFAULT 0 NOT NULL,
    activemission integer DEFAULT 0 NOT NULL,
    mission2_1 integer DEFAULT 0 NOT NULL,
    mission2_2 integer DEFAULT 0 NOT NULL,
    mission2_3 integer DEFAULT 0 NOT NULL,
    mission2_4 integer DEFAULT 0 NOT NULL,
    mission2_5 integer DEFAULT 0 NOT NULL,
    mission2_6 integer DEFAULT 0 NOT NULL,
    mission2_7 integer DEFAULT 0 NOT NULL,
    mission2_8 integer DEFAULT 0 NOT NULL,
    mission2_9 integer DEFAULT 0 NOT NULL,
    mission2_10 integer DEFAULT 0 NOT NULL,
    mission2_11 integer DEFAULT 0 NOT NULL,
    mission2_12 integer DEFAULT 0 NOT NULL,
    mission2_13 integer DEFAULT 0 NOT NULL,
    mission2_14 integer DEFAULT 0 NOT NULL,
    mission2_15 integer DEFAULT 0 NOT NULL,
    mission2_16 integer DEFAULT 0 NOT NULL,
    mission2_17 integer DEFAULT 0 NOT NULL,
    mission2_18 integer DEFAULT 0 NOT NULL,
    mission2_19 integer DEFAULT 0 NOT NULL,
    mission2_20 integer DEFAULT 0 NOT NULL,
    mission2_21 integer DEFAULT 0 NOT NULL,
    mission2_22 integer DEFAULT 0 NOT NULL,
    mission2_23 integer DEFAULT 0 NOT NULL,
    mission2_24 integer DEFAULT 0 NOT NULL,
    mission2_25 integer DEFAULT 0 NOT NULL,
    mission2_26 integer DEFAULT 0 NOT NULL,
    mission2_27 integer DEFAULT 0 NOT NULL,
    mission2_28 integer DEFAULT 0 NOT NULL,
    mission2_29 integer DEFAULT 0 NOT NULL,
    mission2_30 integer DEFAULT 0 NOT NULL,
    mission2_31 integer DEFAULT 0 NOT NULL,
    mission2_32 integer DEFAULT 0 NOT NULL,
    mission2_33 integer DEFAULT 0 NOT NULL,
    mission2_34 integer DEFAULT 0 NOT NULL,
    mission2_35 integer DEFAULT 0 NOT NULL,
    mission2_36 integer DEFAULT 0 NOT NULL,
    mission2_37 integer DEFAULT 0 NOT NULL,
    mission2_38 integer DEFAULT 0 NOT NULL,
    mission2_39 integer DEFAULT 0 NOT NULL,
    mission2_40 integer DEFAULT 0 NOT NULL,
    mission3_1 integer DEFAULT 0 NOT NULL,
    mission3_2 integer DEFAULT 0 NOT NULL,
    mission3_3 integer DEFAULT 0 NOT NULL,
    mission3_4 integer DEFAULT 0 NOT NULL,
    mission3_5 integer DEFAULT 0 NOT NULL,
    mission3_6 integer DEFAULT 0 NOT NULL,
    mission3_7 integer DEFAULT 0 NOT NULL,
    mission3_8 integer DEFAULT 0 NOT NULL,
    mission3_9 integer DEFAULT 0 NOT NULL,
    mission3_10 integer DEFAULT 0 NOT NULL,
    mission3_11 integer DEFAULT 0 NOT NULL,
    mission3_12 integer DEFAULT 0 NOT NULL,
    mission3_13 integer DEFAULT 0 NOT NULL,
    mission3_14 integer DEFAULT 0 NOT NULL,
    mission3_15 integer DEFAULT 0 NOT NULL,
    mission3_16 integer DEFAULT 0 NOT NULL,
    mission3_17 integer DEFAULT 0 NOT NULL,
    mission3_18 integer DEFAULT 0 NOT NULL,
    mission3_19 integer DEFAULT 0 NOT NULL,
    mission3_20 integer DEFAULT 0 NOT NULL,
    mission3_21 integer DEFAULT 0 NOT NULL,
    mission3_22 integer DEFAULT 0 NOT NULL,
    mission3_23 integer DEFAULT 0 NOT NULL,
    mission3_24 integer DEFAULT 0 NOT NULL,
    mission3_25 integer DEFAULT 0 NOT NULL,
    mission3_26 integer DEFAULT 0 NOT NULL,
    mission3_27 integer DEFAULT 0 NOT NULL,
    mission3_28 integer DEFAULT 0 NOT NULL,
    mission3_29 integer DEFAULT 0 NOT NULL,
    mission3_30 integer DEFAULT 0 NOT NULL,
    mission3_31 integer DEFAULT 0 NOT NULL,
    mission3_32 integer DEFAULT 0 NOT NULL,
    mission3_33 integer DEFAULT 0 NOT NULL,
    mission3_34 integer DEFAULT 0 NOT NULL,
    mission3_35 integer DEFAULT 0 NOT NULL,
    mission3_36 integer DEFAULT 0 NOT NULL,
    mission3_37 integer DEFAULT 0 NOT NULL,
    mission3_38 integer DEFAULT 0 NOT NULL,
    mission3_39 integer DEFAULT 0 NOT NULL,
    mission3_40 integer DEFAULT 0 NOT NULL,
    card1 integer DEFAULT 0 NOT NULL,
    card2 integer DEFAULT 0 NOT NULL,
    card3 integer DEFAULT 0 NOT NULL
);
 #   DROP TABLE public.player_missions;
       public         postgres    false    6            Ý            1259    20072    player_stats    TABLE     á  CREATE TABLE player_stats (
    player_id bigint NOT NULL,
    season_fights integer DEFAULT 0 NOT NULL,
    season_wins integer DEFAULT 0 NOT NULL,
    season_losts integer DEFAULT 0 NOT NULL,
    season_kills integer DEFAULT 0 NOT NULL,
    season_deaths integer DEFAULT 0 NOT NULL,
    season_seria_wins integer DEFAULT 0 NOT NULL,
    season_kpd integer DEFAULT 0 NOT NULL,
    season_escapes integer DEFAULT 0 NOT NULL,
    fights integer DEFAULT 0 NOT NULL,
    wins integer DEFAULT 0 NOT NULL,
    losts integer DEFAULT 0 NOT NULL,
    kills integer DEFAULT 0 NOT NULL,
    deaths integer DEFAULT 0 NOT NULL,
    seria_wins integer DEFAULT 0 NOT NULL,
    kpd integer DEFAULT 0 NOT NULL,
    escapes integer DEFAULT 0 NOT NULL
);
     DROP TABLE public.player_stats;
       public         postgres    false    6            Ë           0    0    TABLE player_stats    COMMENT     H   COMMENT ON TABLE player_stats IS 'Ã‘Ã²Ã Ã²Ã¨Ã±Ã²Ã¨ÃªÃ  Ã¨Ã£Ã°Ã®ÃªÃ®Ã¢';
            public       postgres    false    221            Ì           0    0    COLUMN player_stats.player_id    COMMENT     ?   COMMENT ON COLUMN player_stats.player_id IS 'ID Ã¨Ã£Ã°Ã®ÃªÃ ';
            public       postgres    false    221            Í           0    0 !   COLUMN player_stats.season_fights    COMMENT     W   COMMENT ON COLUMN player_stats.season_fights IS 'Ã‚Ã±Ã¥Ã£Ã® Ã¡Ã®Ã¥Ã¢ Ã§Ã  Ã±Ã¥Ã§Ã®Ã­';
            public       postgres    false    221            Î           0    0    COLUMN player_stats.season_wins    COMMENT     W   COMMENT ON COLUMN player_stats.season_wins IS 'Ã‚Ã±Ã¥Ã£Ã® Ã¯Ã®Ã¡Ã¥Ã¤ Ã§Ã  Ã±Ã¥Ã§Ã®Ã­';
            public       postgres    false    221            Ï           0    0     COLUMN player_stats.season_losts    COMMENT     b   COMMENT ON COLUMN player_stats.season_losts IS 'Ã‚Ã±Ã¥Ã£Ã® Ã¯Ã°Ã®Ã¨Ã£Ã°Ã»Ã¸Ã¥Ã© Ã§Ã  Ã±Ã¥Ã§Ã®Ã­';
            public       postgres    false    221            Ð           0    0     COLUMN player_stats.season_kills    COMMENT     X   COMMENT ON COLUMN player_stats.season_kills IS 'Ã‚Ã±Ã¥Ã£Ã® Ã³Ã¡Ã¨Ã²Ã® Ã§Ã  Ã±Ã¥Ã§Ã®Ã­';
            public       postgres    false    221            Ñ           0    0 !   COLUMN player_stats.season_deaths    COMMENT     W   COMMENT ON COLUMN player_stats.season_deaths IS 'Ã‚Ã±Ã¥Ã£Ã® Ã³Ã¬Ã¥Ã° Ã§Ã  Ã±Ã¥Ã§Ã®Ã­';
            public       postgres    false    221            Ò           0    0 %   COLUMN player_stats.season_seria_wins    COMMENT     M   COMMENT ON COLUMN player_stats.season_seria_wins IS 'Ã‘Ã¥Ã°Ã¨Ã¿ Ã¯Ã®Ã¡Ã¥Ã¤';
            public       postgres    false    221            Ó           0    0    COLUMN player_stats.season_kpd    COMMENT     7   COMMENT ON COLUMN player_stats.season_kpd IS 'ÃŠÃÃ„';
            public       postgres    false    221            Ô           0    0 "   COLUMN player_stats.season_escapes    COMMENT     \   COMMENT ON COLUMN player_stats.season_escapes IS 'Ã‚Ã±Ã¥Ã£Ã® Ã±Ã¡Ã¥Ã¦Ã Ã« Ã§Ã  Ã±Ã¥Ã§Ã®Ã­';
            public       postgres    false    221            Õ           0    0    COLUMN player_stats.fights    COMMENT     @   COMMENT ON COLUMN player_stats.fights IS 'Ã‚Ã±Ã¥Ã£Ã® Ã¡Ã®Ã¥Ã¢';
            public       postgres    false    221            Ö           0    0    COLUMN player_stats.wins    COMMENT     @   COMMENT ON COLUMN player_stats.wins IS 'Ã‚Ã±Ã¥Ã£Ã® Ã¯Ã®Ã¡Ã¥Ã¤';
            public       postgres    false    221            ×           0    0    COLUMN player_stats.losts    COMMENT     K   COMMENT ON COLUMN player_stats.losts IS 'Ã‚Ã±Ã¥Ã£Ã® Ã¯Ã°Ã®Ã¨Ã£Ã°Ã»Ã¸Ã¥Ã©';
            public       postgres    false    221            Ø           0    0    COLUMN player_stats.kills    COMMENT     A   COMMENT ON COLUMN player_stats.kills IS 'Ã‚Ã±Ã¥Ã£Ã® Ã³Ã¡Ã¨Ã²Ã®';
            public       postgres    false    221            Ù           0    0    COLUMN player_stats.deaths    COMMENT     @   COMMENT ON COLUMN player_stats.deaths IS 'Ã‚Ã±Ã¥Ã£Ã® Ã³Ã¬Ã¥Ã°';
            public       postgres    false    221            Ú           0    0    COLUMN player_stats.seria_wins    COMMENT     F   COMMENT ON COLUMN player_stats.seria_wins IS 'Ã‘Ã¥Ã°Ã¨Ã¿ Ã¯Ã®Ã¡Ã¥Ã¤';
            public       postgres    false    221            Û           0    0    COLUMN player_stats.kpd    COMMENT     0   COMMENT ON COLUMN player_stats.kpd IS 'ÃŠÃÃ„';
            public       postgres    false    221            Ü           0    0    COLUMN player_stats.escapes    COMMENT     E   COMMENT ON COLUMN player_stats.escapes IS 'Ã‚Ã±Ã¥Ã£Ã® Ã±Ã¡Ã¥Ã¦Ã Ã«';
            public       postgres    false    221            Þ            1259    20091 
   player_titles    TABLE     ¤  CREATE TABLE player_titles (
    owner_id bigint DEFAULT 0 NOT NULL,
    titleequiped1 integer DEFAULT 0 NOT NULL,
    titleequiped2 integer DEFAULT 0 NOT NULL,
    titleequiped3 integer DEFAULT 0 NOT NULL,
    titlepos1 integer DEFAULT 0 NOT NULL,
    titlepos2 integer DEFAULT 0 NOT NULL,
    titlepos3 integer DEFAULT 0 NOT NULL,
    titlepos4 integer DEFAULT 0 NOT NULL,
    titlepos5 integer DEFAULT 0 NOT NULL,
    titlepos6 integer DEFAULT 0 NOT NULL,
    title1 integer DEFAULT 0 NOT NULL,
    title2 integer DEFAULT 0 NOT NULL,
    title3 integer DEFAULT 0 NOT NULL,
    title4 integer DEFAULT 0 NOT NULL,
    title5 integer DEFAULT 0 NOT NULL,
    title6 integer DEFAULT 0 NOT NULL,
    title7 integer DEFAULT 0 NOT NULL,
    title8 integer DEFAULT 0 NOT NULL,
    title9 integer DEFAULT 0 NOT NULL,
    title10 integer DEFAULT 0 NOT NULL,
    title11 integer DEFAULT 0 NOT NULL,
    title12 integer DEFAULT 0 NOT NULL,
    title13 integer DEFAULT 0 NOT NULL,
    title14 integer DEFAULT 0 NOT NULL,
    title15 integer DEFAULT 0 NOT NULL,
    title16 integer DEFAULT 0 NOT NULL,
    title17 integer DEFAULT 0 NOT NULL,
    title18 integer DEFAULT 0 NOT NULL,
    title19 integer DEFAULT 0 NOT NULL,
    title20 integer DEFAULT 0 NOT NULL,
    title21 integer DEFAULT 0 NOT NULL,
    title22 integer DEFAULT 0 NOT NULL,
    title23 integer DEFAULT 0 NOT NULL,
    title24 integer DEFAULT 0 NOT NULL,
    title25 integer DEFAULT 0 NOT NULL,
    title26 integer DEFAULT 0 NOT NULL,
    title27 integer DEFAULT 0 NOT NULL,
    title28 integer DEFAULT 0 NOT NULL,
    title29 integer DEFAULT 0 NOT NULL,
    title30 integer DEFAULT 0 NOT NULL,
    title31 integer DEFAULT 0 NOT NULL,
    title32 integer DEFAULT 0 NOT NULL,
    title33 integer DEFAULT 0 NOT NULL,
    title34 integer DEFAULT 0 NOT NULL,
    title35 integer DEFAULT 0 NOT NULL,
    title36 integer DEFAULT 0 NOT NULL,
    title37 integer DEFAULT 0 NOT NULL,
    title38 integer DEFAULT 0 NOT NULL,
    title39 integer DEFAULT 0 NOT NULL,
    title40 integer DEFAULT 0 NOT NULL,
    title41 integer DEFAULT 0 NOT NULL,
    title42 integer DEFAULT 0 NOT NULL,
    title43 integer DEFAULT 0 NOT NULL,
    title44 integer DEFAULT 0 NOT NULL
);
 !   DROP TABLE public.player_titles;
       public         postgres    false    6            ß            1259    20148    players_id_seq    SEQUENCE     p   CREATE SEQUENCE players_id_seq
    START WITH 8
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;
 %   DROP SEQUENCE public.players_id_seq;
       public       postgres    false    6            à            1259    20150    players    TABLE     ƒ  CREATE TABLE players (
    id bigint DEFAULT nextval('players_id_seq'::regclass) NOT NULL,
    account_id bigint NOT NULL,
    name character varying(35) NOT NULL,
    color integer DEFAULT 0 NOT NULL,
    rank integer DEFAULT 0 NOT NULL,
    gp integer DEFAULT 0 NOT NULL,
    exp integer DEFAULT 0 NOT NULL,
    pc_cafe integer DEFAULT 0 NOT NULL,
    online boolean DEFAULT false NOT NULL,
    mission_id1 integer,
    mission_id2 integer,
    mission_id3 integer,
    title_slot integer,
    brooche integer,
    insignia integer,
    medal integer,
    blue_order integer,
    checks integer DEFAULT 0,
    check_day integer DEFAULT 0
);
    DROP TABLE public.players;
       public         postgres    false    223    6            Ý           0    0 
   TABLE players    COMMENT     ,   COMMENT ON TABLE players IS 'ÃˆÃ£Ã°Ã®ÃªÃ¨';
            public       postgres    false    224            Þ           0    0    COLUMN players.id    COMMENT     3   COMMENT ON COLUMN players.id IS 'ID Ã¨Ã£Ã°Ã®ÃªÃ ';
            public       postgres    false    224            ß           0    0    COLUMN players.account_id    COMMENT     ?   COMMENT ON COLUMN players.account_id IS 'ID Ã ÃªÃªÃ Ã³Ã­Ã²Ã ';
            public       postgres    false    224            à           0    0    COLUMN players.name    COMMENT     ,   COMMENT ON COLUMN players.name IS 'ÃˆÃ¬Ã¿';
            public       postgres    false    224            á           0    0    COLUMN players.color    COMMENT     :   COMMENT ON COLUMN players.color IS 'Ã–Ã¢Ã¥Ã² Ã¨Ã¬Ã¥Ã­Ã¨';
            public       postgres    false    224            â           0    0    COLUMN players.rank    COMMENT     .   COMMENT ON COLUMN players.rank IS 'ÃÃ Ã­Ã£';
            public       postgres    false    224            ã           0    0    COLUMN players.gp    COMMENT     (   COMMENT ON COLUMN players.gp IS 'ÃƒÃ';
            public       postgres    false    224            ä           0    0    COLUMN players.exp    COMMENT     (   COMMENT ON COLUMN players.exp IS 'EXP';
            public       postgres    false    224            å           0    0    COLUMN players.pc_cafe    COMMENT     ,   COMMENT ON COLUMN players.pc_cafe IS 'EXP';
            public       postgres    false    224            æ           0    0    COLUMN players.online    COMMENT     :   COMMENT ON COLUMN players.online IS 'Ã‚ Ã®Ã­Ã«Ã Ã©Ã­Ã¥?';
            public       postgres    false    224            á            1259    20162    settings    TABLE     Á   CREATE TABLE settings (
    type character varying(50) NOT NULL,
    name character varying(50) NOT NULL,
    value character varying(50) NOT NULL,
    regexp character varying(50) NOT NULL
);
    DROP TABLE public.settings;
       public         postgres    false    6            â            1259    20165    store    TABLE        CREATE TABLE store (
    id integer NOT NULL,
    item_id integer NOT NULL,
    nome character varying(255) DEFAULT ''::character varying,
    gold integer NOT NULL,
    cash integer NOT NULL,
    count integer NOT NULL,
    tag integer NOT NULL,
    evento integer DEFAULT 0 NOT NULL
);
    DROP TABLE public.store;
       public         postgres    false    6            ã            1259    20170    store_stock    TABLE       CREATE TABLE store_stock (
    id integer NOT NULL,
    item_id integer NOT NULL,
    nome character varying(255) DEFAULT ''::character varying,
    tipo1 integer NOT NULL,
    tipo2 integer NOT NULL,
    tipo3 integer NOT NULL,
    titulo integer NOT NULL
);
    DROP TABLE public.store_stock;
       public         postgres    false    6            ä            1259    20174    template_items    TABLE     ™   CREATE TABLE template_items (
    template_id bigint NOT NULL,
    item_id bigint NOT NULL,
    count integer NOT NULL,
    equipped integer NOT NULL
);
 "   DROP TABLE public.template_items;
       public         postgres    false    6            ç           0    0    TABLE template_items    COMMENT     5   COMMENT ON TABLE template_items IS 'Ã˜Ã Ã¡Ã«Ã®Ã­Ã»';
            public       postgres    false    228            è           0    0 !   COLUMN template_items.template_id    COMMENT     E   COMMENT ON COLUMN template_items.template_id IS 'id Ã¸Ã Ã¡Ã«Ã®Ã­Ã ';
            public       postgres    false    228            é           0    0    COLUMN template_items.item_id    COMMENT     C   COMMENT ON COLUMN template_items.item_id IS 'id Ã¯Ã°Ã¥Ã¤Ã¬Ã¥Ã²Ã ';
            public       postgres    false    228            ê           0    0    COLUMN template_items.count    COMMENT     L   COMMENT ON COLUMN template_items.count IS 'ÃŠÃ®Ã«-Ã¢Ã® Ã¯Ã°Ã¥Ã¤Ã¬Ã¥Ã²Ã®Ã¢';
            public       postgres    false    228            ë           0    0    COLUMN template_items.equipped    COMMENT     M   COMMENT ON COLUMN template_items.equipped IS 'ÃŽÃ¤Ã¥Ã² Ã«Ã¨ Ã¯Ã°Ã¥Ã¤Ã¬Ã¥Ã²';
            public       postgres    false    228            å            1259    20177    template_other    TABLE     €   CREATE TABLE template_other (
    template_id bigint NOT NULL,
    startmoney integer NOT NULL,
    startgp integer NOT NULL
);
 "   DROP TABLE public.template_other;
       public         postgres    false    6            ì           0    0    TABLE template_other    COMMENT     5   COMMENT ON TABLE template_other IS 'Ã˜Ã Ã¡Ã«Ã®Ã­Ã»';
            public       postgres    false    229            í           0    0 !   COLUMN template_other.template_id    COMMENT     E   COMMENT ON COLUMN template_other.template_id IS 'id Ã¸Ã Ã¡Ã«Ã®Ã­Ã ';
            public       postgres    false    229            î           0    0     COLUMN template_other.startmoney    COMMENT     Q   COMMENT ON COLUMN template_other.startmoney IS 'ÃŠÃ®Ã«-Ã¢Ã® Ã¯Ã°Ã¥Ã¤Ã¬Ã¥Ã²Ã®Ã¢';
            public       postgres    false    229            ï           0    0    COLUMN template_other.startgp    COMMENT     N   COMMENT ON COLUMN template_other.startgp IS 'ÃŠÃ®Ã«-Ã¢Ã® Ã¯Ã°Ã¥Ã¤Ã¬Ã¥Ã²Ã®Ã¢';
            public       postgres    false    229            æ            1259    20180    templates_id_seq    SEQUENCE     r   CREATE SEQUENCE templates_id_seq
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;
 '   DROP SEQUENCE public.templates_id_seq;
       public       postgres    false    6            ç            1259    20182 	   templates    TABLE     á   CREATE TABLE templates (
    id bigint DEFAULT nextval('templates_id_seq'::regclass) NOT NULL,
    date_start timestamp with time zone NOT NULL,
    date_stop timestamp with time zone NOT NULL,
    active boolean NOT NULL
);
    DROP TABLE public.templates;
       public         postgres    false    230    6            ð           0    0    TABLE templates    COMMENT     0   COMMENT ON TABLE templates IS 'Ã˜Ã Ã¡Ã«Ã®Ã­Ã»';
            public       postgres    false    231            ñ           0    0    COLUMN templates.id    COMMENT     7   COMMENT ON COLUMN templates.id IS 'id Ã¸Ã Ã¡Ã«Ã®Ã­Ã ';
            public       postgres    false    231            ò           0    0    COLUMN templates.date_start    COMMENT     A   COMMENT ON COLUMN templates.date_start IS 'id Ã¯Ã°Ã¥Ã¤Ã¬Ã¥Ã²Ã ';
            public       postgres    false    231            ó           0    0    COLUMN templates.date_stop    COMMENT     [   COMMENT ON COLUMN templates.date_stop IS 'Ã’Ã¨Ã¯ Ã±Ã«Ã®Ã²Ã®Ã¢ Ã¢ ÃªÃ®Ã²Ã®Ã°Ã»Ã¥ Ã®Ã¤Ã¥Ã²';
            public       postgres    false    231            ô           0    0    COLUMN templates.active    COMMENT     G   COMMENT ON COLUMN templates.active IS 'Ã€Ã­Ã²Ã¨Ã¢Ã­Ã»Ã© Ã¸Ã Ã¡Ã«Ã®Ã­';
            public       postgres    false    231            /          0    19335    account_access 
   TABLE DATA               3   COPY account_access (accountid, level) FROM stdin;
    public       postgres    false    170   Ü¹      0          0    19338    account_activity 
   TABLE DATA               S   COPY account_activity (account_id, last_active, last_ip, total_active) FROM stdin;
    public       postgres    false    171   ù¹      1          0    19344    account_banned 
   TABLE DATA               X   COPY account_banned (type, value, date_lock, date_unlock, owner_id, reason) FROM stdin;
    public       postgres    false    172   "»      2          0    19347    account_bonuses 
   TABLE DATA               C   COPY account_bonuses (account_id, bonus, bonus_expire) FROM stdin;
    public       postgres    false    173   ?»      4          0    19352    accounts 
   TABLE DATA               O   COPY accounts (id, login, password, email, money, active, mac, ip) FROM stdin;
    public       postgres    false    175   »      õ           0    0    accounts_id_seq    SEQUENCE SET     8   SELECT pg_catalog.setval('accounts_id_seq', 198, true);
            public       postgres    false    174            6          0    19363    channels 
   TABLE DATA               >   COPY channels (id, gameserver_id, type, announce) FROM stdin;
    public       postgres    false    177   [¿      ö           0    0    channels_id_seq    SEQUENCE SET     7   SELECT pg_catalog.setval('channels_id_seq', 1, false);
            public       postgres    false    176            8          0    19369    clans 
   TABLE DATA               ‹   COPY clans (id, name, rank, owner_id, color, logo1, logo2, logo3, logo4, info, notice, create_date, players, max_players, exp) FROM stdin;
    public       postgres    false    179   Ä¿      ÷           0    0    clans_id_seq    SEQUENCE SET     3   SELECT pg_catalog.setval('clans_id_seq', 2, true);
            public       postgres    false    178            :          0    19379    contas 
   TABLE DATA               J   COPY contas (id, login, senha, status, ip, mac, online, data) FROM stdin;
    public       postgres    false    181   «À      ø           0    0 
   contas_seq    SEQUENCE SET     1   SELECT pg_catalog.setval('contas_seq', 1, true);
            public       postgres    false    180            ;          0    19392    event 
   TABLE DATA               F   COPY event (id, type, nome, total, inicio, fim, mensagem) FROM stdin;
    public       postgres    false    182   ÈÀ      <          0    19401 
   event_item 
   TABLE DATA               F   COPY event_item (id, total, item_id, nome, count, active) FROM stdin;
    public       postgres    false    183   Á      =          0    19409 
   event_show 
   TABLE DATA               D   COPY event_show (event, dia, total, item_id1, item_id2) FROM stdin;
    public       postgres    false    184   SÁ      ?          0    19414    gameservers 
   TABLE DATA               ?   COPY gameservers (id, password, type, max_players) FROM stdin;
    public       postgres    false    186   Á      ù           0    0    gameservers_id_seq    SEQUENCE SET     :   SELECT pg_catalog.setval('gameservers_id_seq', 1, false);
            public       postgres    false    185            @          0    19419    goods 
   TABLE DATA               a   COPY goods (good_id, pricecredits, pricepoints, stocktype, title, quantity, item_id) FROM stdin;
    public       postgres    false    187   ÀÁ      A          0    19422    hot_news 
   TABLE DATA               2   COPY hot_news (id, titolo, contenuto) FROM stdin;
    public       postgres    false    188   ZÑ      C          0    19430    ipsystem 
   TABLE DATA               ;   COPY ipsystem (id, type, startpoint, endpoint) FROM stdin;
    public       postgres    false    190   Ñ      ú           0    0    ipsystem_id_seq    SEQUENCE SET     7   SELECT pg_catalog.setval('ipsystem_id_seq', 1, false);
            public       postgres    false    189            E          0    19436    items 
   TABLE DATA               “   COPY items (id, type, slot_type, consume_type, consume_value, repair_credits, repair_points, repair_quantity, c_level, c_value, rb_id) FROM stdin;
    public       postgres    false    192   ªÑ      û           0    0    items_id_seq    SEQUENCE SET     4   SELECT pg_catalog.setval('items_id_seq', 31, true);
            public       postgres    false    191            F          0    19444    jogador 
   TABLE DATA               ø   COPY jogador (id, nick, rank, gold, cash, exp, color, pc_cafe, clan_id, brooch, insignia, medal, blue_order, mission1, mission2, mission3, checks, check_day, minutos, emblema, cor_mira, false_rank, date, access_level, role, false_nick) FROM stdin;
    public       postgres    false    193   Uß      H          0    19477 
   jogador_amigo 
   TABLE DATA               F   COPY jogador_amigo (object, player_id, friend_id, status) FROM stdin;
    public       postgres    false    195   äß      ü           0    0    jogador_amigo_seq    SEQUENCE SET     8   SELECT pg_catalog.setval('jogador_amigo_seq', 1, true);
            public       postgres    false    194            I          0    19481    jogador_clan 
   TABLE DATA               Õ   COPY jogador_clan (id, owner, name, notice, info, rank, logo1, logo2, logo3, logo4, color, partidas, vitorias, derrotas, autoridade, limite_rank, limite_idade, limite_idade2, pontos, vagas, exp, data) FROM stdin;
    public       postgres    false    196   à      J          0    19508    jogador_config 
   TABLE DATA               ¬   COPY jogador_config (player_id, config, sangue, mira, mao, audio1, audio2, audio_enable, sensibilidade, visao, mouse_invertido, msgconvite, chatsusurro, macro) FROM stdin;
    public       postgres    false    197   à      K          0    19511    jogador_equipamento 
   TABLE DATA               ¸   COPY jogador_equipamento (player_id, weapon_primary, weapon_secundary, weapon_melee, weapon_grenade, weapon_special, char_red, char_blue, char_head, char_beret, char_dino) FROM stdin;
    public       postgres    false    198   ;à      L          0    19514    jogador_estatisticas 
   TABLE DATA               m   COPY jogador_estatisticas (player_id, partidas, ganhou, perdeu, matou, morreu, headshots, kitou) FROM stdin;
    public       postgres    false    199   Xà      N          0    19519    jogador_inventario 
   TABLE DATA               U   COPY jogador_inventario (object, player_id, item_id, nome, count, equip) FROM stdin;
    public       postgres    false    201   uà      ý           0    0    jogador_inventario_seq    SEQUENCE SET     =   SELECT pg_catalog.setval('jogador_inventario_seq', 1, true);
            public       postgres    false    200            O          0    19524    jogador_invite 
   TABLE DATA               ;   COPY jogador_invite (clan_id, player_id, date) FROM stdin;
    public       postgres    false    202   ’à      Q          0    19529    jogador_mensagem 
   TABLE DATA               i   COPY jogador_mensagem (object, player_id, recipient_name, texto, type, status, dias, "time") FROM stdin;
    public       postgres    false    204   ¯à      þ           0    0    jogador_mensagem_seq    SEQUENCE SET     <   SELECT pg_catalog.setval('jogador_mensagem_seq', 1, false);
            public       postgres    false    203            R          0    19538    jogador_missoes 
   TABLE DATA               G  COPY jogador_missoes (player_id, mission1_1, mission1_2, mission1_3, mission1_4, mission1_5, mission1_6, mission1_7, mission1_8, mission1_9, mission1_10, mission1_11, mission1_12, mission1_13, mission1_14, mission1_15, mission1_16, mission1_17, mission1_18, mission1_19, mission1_20, mission1_21, mission1_22, mission1_23, mission1_24, mission1_25, mission1_26, mission1_27, mission1_28, mission1_29, mission1_30, mission1_31, mission1_32, mission1_33, mission1_34, mission1_35, mission1_36, mission1_37, mission1_38, mission1_39, mission1_40, mission2_1, mission2_2, mission2_3, mission2_4, mission2_5, mission2_6, mission2_7, mission2_8, mission2_9, mission2_10, mission2_11, mission2_12, mission2_13, mission2_14, mission2_15, mission2_16, mission2_17, mission2_18, mission2_19, mission2_20, mission2_21, mission2_22, mission2_23, mission2_24, mission2_25, mission2_26, mission2_27, mission2_28, mission2_29, mission2_30, mission2_31, mission2_32, mission2_33, mission2_34, mission2_35, mission2_36, mission2_37, mission2_38, mission2_39, mission2_40, mission3_1, mission3_2, mission3_3, mission3_4, mission3_5, mission3_6, mission3_7, mission3_8, mission3_9, mission3_10, mission3_11, mission3_12, mission3_13, mission3_14, mission3_15, mission3_16, mission3_17, mission3_18, mission3_19, mission3_20, mission3_21, mission3_22, mission3_23, mission3_24, mission3_25, mission3_26, mission3_27, mission3_28, mission3_29, mission3_30, mission3_31, mission3_32, mission3_33, mission3_34, mission3_35, mission3_36, mission3_37, mission3_38, mission3_39, mission3_40, card1, card2, card3, active) FROM stdin;
    public       postgres    false    205   Ìà      S          0    19666    jogador_teclado 
   TABLE DATA               T  COPY jogador_teclado (player_id, k_esquerda, k_direita, k_frente, k_atras, k_pular, k_andar, k_agachar, k_o_atr, k_atirar, k_scope, k_recarregar, k_trc_arm, k_arm_qq, k_arm_ant, k_arm_pos, k_jog_arm, k_placar, k_mapa, k_mapa_pos, k_mapa_ant, k_chat, k_chat_g, k_chat_t, k_chat_hz, k_chat_v, k_chat_c, k_rad_t, k_rad_p, k_rad_i, k_bomb_d, k_sen_pos, k_sen_ant, k_print, k_mira_x, k_gravar, k_valor1, k_valor2, k_valor3, k_valor4, k_macro_e, armas1, armas2, armas3, armas4, armas5, armas6, macro1, macro2, macro3, macro4, macro5, macrolength1, macrolength2, macrolength3, macrolength4) FROM stdin;
    public       postgres    false    206   éà      T          0    19727    jogador_teclado2 
   TABLE DATA               '  COPY jogador_teclado2 (player_id, v_1, v_2, v_3, v_4, v_5, v_6, v_7, v_8, v_9, v_10, v_11, v_12, v_13, v_14, v_15, v_16, v_17, v_18, v_19, v_20, v_21, v_22, v_23, v_24, v_25, v_26, v_27, v_28, v_29, v_30, v_31, v_32, v_33, v_34, v_35, v_36, v_37, v_38, v_39, v_40, v_41, v_42, v_43) FROM stdin;
    public       postgres    false    207   á      U          0    19773    jogador_titulos 
   TABLE DATA               ò  COPY jogador_titulos (player_id, slot, equip1, equip2, equip3, pos1, pos2, pos3, pos4, pos5, pos6, title1, title2, title3, title4, title5, title6, title7, title8, title9, title10, title11, title12, title13, title14, title15, title16, title17, title18, title19, title20, title21, title22, title23, title24, title25, title26, title27, title28, title29, title30, title31, title32, title33, title34, title35, title36, title37, title38, title39, title40, title41, title42, title43, title44) FROM stdin;
    public       postgres    false    208   #á      V          0    19776    levelup 
   TABLE DATA               P   COPY levelup (rank, "needExp", "allExp", "rewardGP", "rewardItems") FROM stdin;
    public       postgres    false    209   @á      W          0    19782    missions 
   TABLE DATA               F  COPY missions (owner_id, mission1_1, mission1_2, mission1_3, mission1_4, mission1_5, mission1_6, mission1_7, mission1_8, mission1_9, mission1_10, mission1_11, mission1_12, mission1_13, mission1_14, mission1_15, mission1_16, mission1_17, mission1_18, mission1_19, mission1_20, mission1_21, mission1_22, mission1_23, mission1_24, mission1_25, mission1_26, mission1_27, mission1_28, mission1_29, mission1_30, mission1_31, mission1_32, mission1_33, mission1_34, mission1_35, mission1_36, mission1_37, mission1_38, mission1_39, mission1_40, activemission, mission2_1, mission2_2, mission2_3, mission2_4, mission2_5, mission2_6, mission2_7, mission2_8, mission2_9, mission2_10, mission2_11, mission2_12, mission2_13, mission2_14, mission2_15, mission2_16, mission2_17, mission2_18, mission2_19, mission2_20, mission2_21, mission2_22, mission2_23, mission2_24, mission2_25, mission2_26, mission2_27, mission2_28, mission2_29, mission2_30, mission2_31, mission2_32, mission2_33, mission2_34, mission2_35, mission2_36, mission2_37, mission2_38, mission2_39, mission2_40, mission3_1, mission3_2, mission3_3, mission3_4, mission3_5, mission3_6, mission3_7, mission3_8, mission3_9, mission3_10, mission3_11, mission3_12, mission3_13, mission3_14, mission3_15, mission3_16, mission3_17, mission3_18, mission3_19, mission3_20, mission3_21, mission3_22, mission3_23, mission3_24, mission3_25, mission3_26, mission3_27, mission3_28, mission3_29, mission3_30, mission3_31, mission3_32, mission3_33, mission3_34, mission3_35, mission3_36, mission3_37, mission3_38, mission3_39, mission3_40, card1, card2, card3) FROM stdin;
    public       postgres    false    210   ýâ      X          0    19910    news 
   TABLE DATA               <   COPY news (id, titolo, data, autore, contenuto) FROM stdin;
    public       postgres    false    211   ã      Y          0    19916    player_bonus 
   TABLE DATA               >   COPY player_bonus (exp, gold, inicio, fim, ativo) FROM stdin;
    public       postgres    false    212   7ã      Z          0    19924    player_clan 
   TABLE DATA               8   COPY player_clan (clan_id, player_id, rank) FROM stdin;
    public       postgres    false    213   lã      [          0    19927 
   player_config 
   TABLE DATA               q   COPY player_config (playerid, mira, audio, audio1, audio2, vision, sensibility, mao, sangue, config) FROM stdin;
    public       postgres    false    214   ªã      ]          0    19932    player_eqipment 
   TABLE DATA               \   COPY player_eqipment (id, player_id, item_id, count, loc, consume_lost, status) FROM stdin;
    public       postgres    false    216   iä      ÿ           0    0    player_eqipment_id_seq    SEQUENCE SET     @   SELECT pg_catalog.setval('player_eqipment_id_seq', 9139, true);
            public       postgres    false    215            _          0    19938    player_friends 
   TABLE DATA               ?   COPY player_friends (player_id, friend_id, status) FROM stdin;
    public       postgres    false    218                     0    0 $   player_friends_player_account_id_seq    SEQUENCE SET     L   SELECT pg_catalog.setval('player_friends_player_account_id_seq', 1, false);
            public       postgres    false    217                       0    0    player_message_seq    SEQUENCE SET     :   SELECT pg_catalog.setval('player_message_seq', 33, true);
            public       postgres    false    219            a          0    19944    player_missions 
   TABLE DATA               M  COPY player_missions (owner_id, mission1_1, mission1_2, mission1_3, mission1_4, mission1_5, mission1_6, mission1_7, mission1_8, mission1_9, mission1_10, mission1_11, mission1_12, mission1_13, mission1_14, mission1_15, mission1_16, mission1_17, mission1_18, mission1_19, mission1_20, mission1_21, mission1_22, mission1_23, mission1_24, mission1_25, mission1_26, mission1_27, mission1_28, mission1_29, mission1_30, mission1_31, mission1_32, mission1_33, mission1_34, mission1_35, mission1_36, mission1_37, mission1_38, mission1_39, mission1_40, activemission, mission2_1, mission2_2, mission2_3, mission2_4, mission2_5, mission2_6, mission2_7, mission2_8, mission2_9, mission2_10, mission2_11, mission2_12, mission2_13, mission2_14, mission2_15, mission2_16, mission2_17, mission2_18, mission2_19, mission2_20, mission2_21, mission2_22, mission2_23, mission2_24, mission2_25, mission2_26, mission2_27, mission2_28, mission2_29, mission2_30, mission2_31, mission2_32, mission2_33, mission2_34, mission2_35, mission2_36, mission2_37, mission2_38, mission2_39, mission2_40, mission3_1, mission3_2, mission3_3, mission3_4, mission3_5, mission3_6, mission3_7, mission3_8, mission3_9, mission3_10, mission3_11, mission3_12, mission3_13, mission3_14, mission3_15, mission3_16, mission3_17, mission3_18, mission3_19, mission3_20, mission3_21, mission3_22, mission3_23, mission3_24, mission3_25, mission3_26, mission3_27, mission3_28, mission3_29, mission3_30, mission3_31, mission3_32, mission3_33, mission3_34, mission3_35, mission3_36, mission3_37, mission3_38, mission3_39, mission3_40, card1, card2, card3) FROM stdin;
    public       postgres    false    220   :      b          0    20072    player_stats 
   TABLE DATA               Þ   COPY player_stats (player_id, season_fights, season_wins, season_losts, season_kills, season_deaths, season_seria_wins, season_kpd, season_escapes, fights, wins, losts, kills, deaths, seria_wins, kpd, escapes) FROM stdin;
    public       postgres    false    221   õ      c          0    20091 
   player_titles 
   TABLE DATA                 COPY player_titles (owner_id, titleequiped1, titleequiped2, titleequiped3, titlepos1, titlepos2, titlepos3, titlepos4, titlepos5, titlepos6, title1, title2, title3, title4, title5, title6, title7, title8, title9, title10, title11, title12, title13, title14, title15, title16, title17, title18, title19, title20, title21, title22, title23, title24, title25, title26, title27, title28, title29, title30, title31, title32, title33, title34, title35, title36, title37, title38, title39, title40, title41, title42, title43, title44) FROM stdin;
    public       postgres    false    222   É      e          0    20150    players 
   TABLE DATA               Ã   COPY players (id, account_id, name, color, rank, gp, exp, pc_cafe, online, mission_id1, mission_id2, mission_id3, title_slot, brooche, insignia, medal, blue_order, checks, check_day) FROM stdin;
    public       postgres    false    224   e                 0    0    players_id_seq    SEQUENCE SET     7   SELECT pg_catalog.setval('players_id_seq', 198, true);
            public       postgres    false    223            f          0    20162    settings 
   TABLE DATA               6   COPY settings (type, name, value, regexp) FROM stdin;
    public       postgres    false    225   š      g          0    20165    store 
   TABLE DATA               K   COPY store (id, item_id, nome, gold, cash, count, tag, evento) FROM stdin;
    public       postgres    false    226   ·      h          0    20170    store_stock 
   TABLE DATA               N   COPY store_stock (id, item_id, nome, tipo1, tipo2, tipo3, titulo) FROM stdin;
    public       postgres    false    227   £2      i          0    20174    template_items 
   TABLE DATA               H   COPY template_items (template_id, item_id, count, equipped) FROM stdin;
    public       postgres    false    228   ›<      j          0    20177    template_other 
   TABLE DATA               C   COPY template_other (template_id, startmoney, startgp) FROM stdin;
    public       postgres    false    229   =      l          0    20182 	   templates 
   TABLE DATA               ?   COPY templates (id, date_start, date_stop, active) FROM stdin;
    public       postgres    false    231   B=                 0    0    templates_id_seq    SEQUENCE SET     8   SELECT pg_catalog.setval('templates_id_seq', 1, false);
            public       postgres    false    230            †
           2606    20187    account_activity_account_id_key 
   CONSTRAINT     j   ALTER TABLE ONLY account_activity
    ADD CONSTRAINT account_activity_account_id_key UNIQUE (account_id);
 Z   ALTER TABLE ONLY public.account_activity DROP CONSTRAINT account_activity_account_id_key;
       public         postgres    false    171    171            ˆ
           2606    20189    accounts_email_key 
   CONSTRAINT     P   ALTER TABLE ONLY accounts
    ADD CONSTRAINT accounts_email_key UNIQUE (email);
 E   ALTER TABLE ONLY public.accounts DROP CONSTRAINT accounts_email_key;
       public         postgres    false    175    175            Š
           2606    20191    accounts_login_key 
   CONSTRAINT     P   ALTER TABLE ONLY accounts
    ADD CONSTRAINT accounts_login_key UNIQUE (login);
 E   ALTER TABLE ONLY public.accounts DROP CONSTRAINT accounts_login_key;
       public         postgres    false    175    175            Ž
           2606    20193    channels_id_gameserver_id_key 
   CONSTRAINT     g   ALTER TABLE ONLY channels
    ADD CONSTRAINT channels_id_gameserver_id_key UNIQUE (id, gameserver_id);
 P   ALTER TABLE ONLY public.channels DROP CONSTRAINT channels_id_gameserver_id_key;
       public         postgres    false    177    177    177            
           2606    20195    clans_name_key 
   CONSTRAINT     H   ALTER TABLE ONLY clans
    ADD CONSTRAINT clans_name_key UNIQUE (name);
 >   ALTER TABLE ONLY public.clans DROP CONSTRAINT clans_name_key;
       public         postgres    false    179    179            ’
           2606    20197    clans_owner_id_key 
   CONSTRAINT     P   ALTER TABLE ONLY clans
    ADD CONSTRAINT clans_owner_id_key UNIQUE (owner_id);
 B   ALTER TABLE ONLY public.clans DROP CONSTRAINT clans_owner_id_key;
       public         postgres    false    179    179            š
           2606    20199    items_id_key 
   CONSTRAINT     D   ALTER TABLE ONLY items
    ADD CONSTRAINT items_id_key UNIQUE (id);
 <   ALTER TABLE ONLY public.items DROP CONSTRAINT items_id_key;
       public         postgres    false    192    192            œ
           2606    20201    levelup_rank_key 
   CONSTRAINT     L   ALTER TABLE ONLY levelup
    ADD CONSTRAINT levelup_rank_key UNIQUE (rank);
 B   ALTER TABLE ONLY public.levelup DROP CONSTRAINT levelup_rank_key;
       public         postgres    false    209    209            „
           2606    20203    pk_account_access 
   CONSTRAINT     ^   ALTER TABLE ONLY account_access
    ADD CONSTRAINT pk_account_access PRIMARY KEY (accountid);
 J   ALTER TABLE ONLY public.account_access DROP CONSTRAINT pk_account_access;
       public         postgres    false    170    170            Œ
           2606    20205    pk_accounts 
   CONSTRAINT     K   ALTER TABLE ONLY accounts
    ADD CONSTRAINT pk_accounts PRIMARY KEY (id);
 >   ALTER TABLE ONLY public.accounts DROP CONSTRAINT pk_accounts;
       public         postgres    false    175    175            ”
           2606    20207    pk_clans 
   CONSTRAINT     E   ALTER TABLE ONLY clans
    ADD CONSTRAINT pk_clans PRIMARY KEY (id);
 8   ALTER TABLE ONLY public.clans DROP CONSTRAINT pk_clans;
       public         postgres    false    179    179            –
           2606    20209    pk_gameservers 
   CONSTRAINT     Q   ALTER TABLE ONLY gameservers
    ADD CONSTRAINT pk_gameservers PRIMARY KEY (id);
 D   ALTER TABLE ONLY public.gameservers DROP CONSTRAINT pk_gameservers;
       public         postgres    false    186    186            ˜
           2606    20211    pk_ipsystem 
   CONSTRAINT     K   ALTER TABLE ONLY ipsystem
    ADD CONSTRAINT pk_ipsystem PRIMARY KEY (id);
 >   ALTER TABLE ONLY public.ipsystem DROP CONSTRAINT pk_ipsystem;
       public         postgres    false    190    190             
           2606    20213    pk_player_eqipment 
   CONSTRAINT     ^   ALTER TABLE ONLY player_eqipment
    ADD CONSTRAINT pk_player_eqipment PRIMARY KEY (id, loc);
 L   ALTER TABLE ONLY public.player_eqipment DROP CONSTRAINT pk_player_eqipment;
       public         postgres    false    216    216    216            ¬
           2606    20215 
   pk_players 
   CONSTRAINT     I   ALTER TABLE ONLY players
    ADD CONSTRAINT pk_players PRIMARY KEY (id);
 <   ALTER TABLE ONLY public.players DROP CONSTRAINT pk_players;
       public         postgres    false    224    224            °
           2606    20217    pk_settings 
   CONSTRAINT     M   ALTER TABLE ONLY settings
    ADD CONSTRAINT pk_settings PRIMARY KEY (name);
 >   ALTER TABLE ONLY public.settings DROP CONSTRAINT pk_settings;
       public         postgres    false    225    225            ²
           2606    20219    pk_templates 
   CONSTRAINT     M   ALTER TABLE ONLY templates
    ADD CONSTRAINT pk_templates PRIMARY KEY (id);
 @   ALTER TABLE ONLY public.templates DROP CONSTRAINT pk_templates;
       public         postgres    false    231    231            ž
           2606    20221    player_clan_player_id_key 
   CONSTRAINT     ^   ALTER TABLE ONLY player_clan
    ADD CONSTRAINT player_clan_player_id_key UNIQUE (player_id);
 O   ALTER TABLE ONLY public.player_clan DROP CONSTRAINT player_clan_player_id_key;
       public         postgres    false    213    213            ¢
           2606    20223 %   player_eqipment_player_id_item_id_key 
   CONSTRAINT        ALTER TABLE ONLY player_eqipment
    ADD CONSTRAINT player_eqipment_player_id_item_id_key UNIQUE (player_id, item_id, status);
 _   ALTER TABLE ONLY public.player_eqipment DROP CONSTRAINT player_eqipment_player_id_item_id_key;
       public         postgres    false    216    216    216    216            ¤
           2606    20225 .   player_friends_player_account_id_friend_id_key 
   CONSTRAINT        ALTER TABLE ONLY player_friends
    ADD CONSTRAINT player_friends_player_account_id_friend_id_key UNIQUE (player_id, friend_id);
 g   ALTER TABLE ONLY public.player_friends DROP CONSTRAINT player_friends_player_account_id_friend_id_key;
       public         postgres    false    218    218    218            ¦
           2606    20227 $   player_friends_player_account_id_key 
   CONSTRAINT     l   ALTER TABLE ONLY player_friends
    ADD CONSTRAINT player_friends_player_account_id_key UNIQUE (player_id);
 ]   ALTER TABLE ONLY public.player_friends DROP CONSTRAINT player_friends_player_account_id_key;
       public         postgres    false    218    218            ¨
           2606    20229    player_stats_player_id_key 
   CONSTRAINT     `   ALTER TABLE ONLY player_stats
    ADD CONSTRAINT player_stats_player_id_key UNIQUE (player_id);
 Q   ALTER TABLE ONLY public.player_stats DROP CONSTRAINT player_stats_player_id_key;
       public         postgres    false    221    221            ª
           2606    20231    player_titles_pkey 
   CONSTRAINT     ]   ALTER TABLE ONLY player_titles
    ADD CONSTRAINT player_titles_pkey PRIMARY KEY (owner_id);
 J   ALTER TABLE ONLY public.player_titles DROP CONSTRAINT player_titles_pkey;
       public         postgres    false    222    222            ®
           2606    20233    players_account_id_key 
   CONSTRAINT     X   ALTER TABLE ONLY players
    ADD CONSTRAINT players_account_id_key UNIQUE (account_id);
 H   ALTER TABLE ONLY public.players DROP CONSTRAINT players_account_id_key;
       public         postgres    false    224    224            Â
           2620    20234    insert_account_activity    TRIGGER     z   CREATE TRIGGER insert_account_activity AFTER INSERT ON accounts FOR EACH ROW EXECUTE PROCEDURE insert_account_activity();
 9   DROP TRIGGER insert_account_activity ON public.accounts;
       public       postgres    false    239    175            Ã
           2620    20235    insert_player_stats    TRIGGER     q   CREATE TRIGGER insert_player_stats AFTER INSERT ON players FOR EACH ROW EXECUTE PROCEDURE insert_player_stats();
 4   DROP TRIGGER insert_player_stats ON public.players;
       public       postgres    false    246    224            ³
           2606    20236    account_activity_account 
   FK CONSTRAINT     €   ALTER TABLE ONLY account_activity
    ADD CONSTRAINT account_activity_account FOREIGN KEY (account_id) REFERENCES accounts(id);
 S   ALTER TABLE ONLY public.account_activity DROP CONSTRAINT account_activity_account;
       public       postgres    false    171    175    2700            ´
           2606    20241    account_bonuses_account 
   FK CONSTRAINT     ~   ALTER TABLE ONLY account_bonuses
    ADD CONSTRAINT account_bonuses_account FOREIGN KEY (account_id) REFERENCES accounts(id);
 Q   ALTER TABLE ONLY public.account_bonuses DROP CONSTRAINT account_bonuses_account;
       public       postgres    false    173    175    2700            µ
           2606    20246    channel_id_gameserver_id 
   FK CONSTRAINT     ~   ALTER TABLE ONLY channels
    ADD CONSTRAINT channel_id_gameserver_id FOREIGN KEY (gameserver_id) REFERENCES gameservers(id);
 K   ALTER TABLE ONLY public.channels DROP CONSTRAINT channel_id_gameserver_id;
       public       postgres    false    177    186    2710            ¶
           2606    20251    clans_player 
   FK CONSTRAINT     f   ALTER TABLE ONLY clans
    ADD CONSTRAINT clans_player FOREIGN KEY (owner_id) REFERENCES players(id);
 <   ALTER TABLE ONLY public.clans DROP CONSTRAINT clans_player;
       public       postgres    false    224    2732    179            ¾
           2606    20256    player_account 
   FK CONSTRAINT     m   ALTER TABLE ONLY players
    ADD CONSTRAINT player_account FOREIGN KEY (account_id) REFERENCES accounts(id);
 @   ALTER TABLE ONLY public.players DROP CONSTRAINT player_account;
       public       postgres    false    2700    175    224            ·
           2606    20261    player_clan_clan 
   FK CONSTRAINT     m   ALTER TABLE ONLY player_clan
    ADD CONSTRAINT player_clan_clan FOREIGN KEY (clan_id) REFERENCES clans(id);
 F   ALTER TABLE ONLY public.player_clan DROP CONSTRAINT player_clan_clan;
       public       postgres    false    213    179    2708            ¸
           2606    20266    player_clan_player 
   FK CONSTRAINT     s   ALTER TABLE ONLY player_clan
    ADD CONSTRAINT player_clan_player FOREIGN KEY (player_id) REFERENCES players(id);
 H   ALTER TABLE ONLY public.player_clan DROP CONSTRAINT player_clan_player;
       public       postgres    false    213    224    2732            ¹
           2606    20271    player_eqipment_item 
   FK CONSTRAINT     u   ALTER TABLE ONLY player_eqipment
    ADD CONSTRAINT player_eqipment_item FOREIGN KEY (item_id) REFERENCES items(id);
 N   ALTER TABLE ONLY public.player_eqipment DROP CONSTRAINT player_eqipment_item;
       public       postgres    false    216    2714    192            º
           2606    20276    player_eqipment_player 
   FK CONSTRAINT     {   ALTER TABLE ONLY player_eqipment
    ADD CONSTRAINT player_eqipment_player FOREIGN KEY (player_id) REFERENCES players(id);
 P   ALTER TABLE ONLY public.player_eqipment DROP CONSTRAINT player_eqipment_player;
       public       postgres    false    216    2732    224            »
           2606    20281 
   player_friend 
   FK CONSTRAINT     q   ALTER TABLE ONLY player_friends
    ADD CONSTRAINT player_friend FOREIGN KEY (friend_id) REFERENCES players(id);
 F   ALTER TABLE ONLY public.player_friends DROP CONSTRAINT player_friend;
       public       postgres    false    218    224    2732            ¼
           2606    20286 
   player_player 
   FK CONSTRAINT     q   ALTER TABLE ONLY player_friends
    ADD CONSTRAINT player_player FOREIGN KEY (player_id) REFERENCES players(id);
 F   ALTER TABLE ONLY public.player_friends DROP CONSTRAINT player_player;
       public       postgres    false    224    218    2732            ½
           2606    20291    player_stats_player 
   FK CONSTRAINT     u   ALTER TABLE ONLY player_stats
    ADD CONSTRAINT player_stats_player FOREIGN KEY (player_id) REFERENCES players(id);
 J   ALTER TABLE ONLY public.player_stats DROP CONSTRAINT player_stats_player;
       public       postgres    false    2732    221    224            ¿
           2606    20296    template_item_item 
   FK CONSTRAINT     r   ALTER TABLE ONLY template_items
    ADD CONSTRAINT template_item_item FOREIGN KEY (item_id) REFERENCES items(id);
 K   ALTER TABLE ONLY public.template_items DROP CONSTRAINT template_item_item;
       public       postgres    false    2714    192    228            À
           2606    20301    template_item_template_i 
   FK CONSTRAINT     €   ALTER TABLE ONLY template_items
    ADD CONSTRAINT template_item_template_i FOREIGN KEY (template_id) REFERENCES templates(id);
 Q   ALTER TABLE ONLY public.template_items DROP CONSTRAINT template_item_template_i;
       public       postgres    false    2738    228    231            Á
           2606    20306    template_other_template_i 
   FK CONSTRAINT        ALTER TABLE ONLY template_other
    ADD CONSTRAINT template_other_template_i FOREIGN KEY (template_id) REFERENCES templates(id);
 R   ALTER TABLE ONLY public.template_other DROP CONSTRAINT template_other_template_i;
       public       postgres    false    2738    229    231            /   
   xœ‹Ñãââ Å ©      0     xœmÒAŽÃ0ÐurŠìGA|ÀÆp–¹ÿ9†tª¦­-/ýd}óû&?yœèz6K6Òðö
âÄu°ñÔSZbP3iÜÔH6OVê‰~QÑå“9†Înm‡peMkÄâ}Örë8 ×Û¢Ô¼7o³Ö§ŽG’úœåuß ³¶
œ2DR;õÅ4F{Qåƒ£\
ˆeAýiý‘x,è³ÈÉíªƒG%&^-¾d½«Je&üNER"™IæÿnYÛ0*fªl®8äƒFmMZÝêÜAè;­~¯ÒÅ¨ÂnZåÚµŽÒ)|Ì´}ÓžVSÅ"@_ÐúÖýVM5þZñESq7¾ÖÐZšæü¥}ßÿ [.¤±      1   
   xœ‹Ñãââ Å ©      2   >   xœmÊ±
€0EÁ:ž‚½ƒìxöŸÑ¤ÊÕ§|šð µ¢“Ý94ëÎr„i­Ü¬Yƒ½—™}`Š™      4   ¾  xœUÉnc9<+ÿ2"EŠ’NY:>úhM^Çq'™äë‡v–¶Ý>Ø>Y,V±ÍÈ›M_h9²ØPº
¡xìû°­öÌaÂ >Þ_æ·¼jyªOÆš³Éaº¥„·iáR¸5ÈÃ$2Aä`r{œWhð ï+çš½ËÀ2¤X+^¸¢)ç>Þ_Þ=æyù…óãïmc¤	,LÁkc4/ýù¥oÀP&ÉÐPtVÁa{ÜBaˆ„‘;åìà³`¯õ–]ÔöÖ¦Å"ùE’Eº¢¤S Êdõ
ÅúË{j¤JýÞaÀê\÷]9
a8Z=ö÷—ër—ûó*ÚíG±V¯Ëå~{óÐÇ2²¥Yì
<ªcðìTŽ¬2på^K+¥÷aÞ5Èm&¬Þ$ú–˜ÒÒ­$Š;=pŒ“S*v·„ó‰ìÄ€#1ŽÙu…óÛ®²~ïþyÝÌëƒ%‰‡xjIÁ¬æzÿd\iµ•.™Éµ2ˆgh[ÏƒZ¦âj• ñýùñzþ˜Üíòýûù6}^µÇ¼5ÔÛÞzÐzoI‘noÒUHþ:!m­Å¼ó/N>LÀzÑ™v?kõ H«j¬4(Œâ}´5ÄèGôÍ¹­W÷÷û‚OS©M^’]¤ëT…s<‰Ð*šõÃú¯ŸOmVsŽkC[<÷nkF—IÊÐ{dŽ1gW!—ú»ä4æIŠÎO  A—ÙäÕÏyuWïóæáÕ4[qÔê*ûK­1Çè3« œµ»P¤T@³ˆl‘‰”aZ(þMr1áÍ9°"‡‰ƒ"ƒù•ÇlÕNGiØÑ PÇô¨õZúÈê”¡—V²ôUqˆHþàz›n`Ç&p2!èeEoÖe½™ÿÍ/ÝX šrˆ¤ÉcÉºPƒf³-=ÅI‰~—‚ZûqÍìÓ7%)éÊ'ºÞ¢MÈê^«)ƒ)ù¡/5ŸË@ÎÅê@¡@–æSÓhÌ¥G+ 4¼| 	þÃFJ0Ü¤kIî:]ï‹*gœ$*œ5êúþßÓ¦Îš"gºWt ëH¬;KP1›ùùany¥½6³±C@Üöþ¥s!ñ¥uFµ2ÖÑsAwTvd&»%t"¢Y?¹år~`%I.tm¯'1;öPªw5B,AÏõ†jØ«9ÌýøJ$ó¸¿äüØß=?ì#G8ÉÌûý¼ª5ÎÖé«äðà£gËõðPØOÐóóóêÉy´§–õcº¸¸ø¿`³      6   Y   xœ3à4ätru÷ôs
æä² òœ}ý8¹QÄÍAâŽ¾žþ~Ážœ\f@×ˆ × xCN.S ÏÏ?È×ÑÄ3Aá£ðŒPx–pûbô¸¸¸ ô;      8   ×   xœ=ÎÏNÃ0ð³ûéL±›Òö¸MÓN@E‘8 ª¬‘±hù3…thoOÆ ú$Ÿ>ÿìª-Gíy±ñ¶rÎIÛ)N‚?ØòA$íØ—e	@ÙRuî
áu{ÿ>®ƒs“7éJeªÎD—;w5$ý•n›ˆÔýoô«~xÜïÍÎ°Í}ìÔuæ(	Dð¢í.8-žƒèƒñieÙEÍ™“ƒŽgÿX’3«†ÄOãÃæÓò¸ŒîU6Û6Û
 üýOÁ÷ñü,ä³7ámQÅM3D[      :   
   xœ‹Ñãââ Å ©      ;   8   xœ31à4àNÍJTHJÍÕ-ËÌKÉWä4ç44×50# ‚r

uŒuM-9¹bô¸¸¸ ¡†R      <   3   xœ31à4ä44 cCSÎ`g]#C÷üœcN#SK#N3®=... ÄÒ^      =   ,   xœ3ä4B3SN.CN# Û Ì2†³Là,S8ËÎ2‡²bô¸¸¸ g%	      ?   !   xœ3ä,I-.áôóòuô‰7ä460àŠÑãââ VF«      @   Š  xœ¥\[²&'~þ]LJð¾—ìûfªf*Éœ4_#"" } ÒŸ!ÿâ3ýL÷Ðß ” ?%Æ”TñJù'bÐ˜Ø›0Â	Ú¤
B,Ù 
1u”áï  $b.q‚òT0$þ©ÄX™Ø‹È´IÄ‚§X'¨>@mƒ
ƒÆTô¨V3È·áRÐ&mPú­Wùïö ¥P#Ncd@Y ©§Mš ¼@}ðå;E‰K¦ô ah#7#À©‚M½1g×¨oB'cˆm‚ O+ÈSðM
 óæÿÿå.+'êü]Ï'$g"Ï'$9tA¢è±õ÷8¢Ã	nŒ€òaÒ.ð8øö8ÐlQäù„dfØã"Ï7„¸´j@öœ‹3ç²!l
M¶á"ÏÀà=#yG\Ö°‡Ñ¿Ô ‹ÿò á5~¨P6ŸJ¬é‡Â+GkÑ^#
eÍšÀr&+‹MQh¢¦½’YQÓàÀ…J&jnhpD½G´QS‘Gäÿk¯EXLF'ï·¨ñCm=‹3©4<ôP»ûî(ªGí%ôêK5×/2TòÝT@Ìíˆq#´´gfê¹ÎÌæÊ ¹x±}”Uó{gáµ³ÚýYÞÛFžoq)ß-<6t^Ž «Yêˆ~dq‹a.À+ âJ¾ŠÁD<êoS½H‚Ð6n‹mõ'pé	e¡âß]:yª€ð»txíñ,»—Ü?“:iÎã=ýƒ¹cÉì…`/ÆB–{[#àW6f:J½	$€}B™#ä¼×!ä9­c6ç™Ø×‘/ÎÙWíGõûæò<@9(š¼ÁðÉ#‡zX¦‘öaÃöžÞãËóÐºg‡J¥€Áœ‘ùÇ0ê^çÛ2Í@	(êÉ¢/;(%<Ñsp¢cÑ¢ÏS&5>.?GG®%¤aêrMäsµèk š@Ëÿõ~Ê¡¥=…Ü…ÎÜV¬÷UÁŠ¹Ñ¤ÐÑôC‹N¡Á‰NüóaþCi§ñ{(¦þ2¿bÎ_ß¡ÈìGÐÔïâÏ~4š¤Bû/šV!GÛ	ÀéW· KHÖ!X“XkÙŸ©RÀ Ç(1Õ¤Z&_jn#]ÅZ<(©Òû§mš)î8mó\C5ß×]@‰ iEz\°|z"?k™ZIé¸Éè´2Õ§›<†z2ò¡—Óôè0Åÿœš›lM‚>8mrÉä¯ê#?912|4ÐÐt’*ÿØ	£yÌÅ™<V8u9‹i­TzhT%%ŒMÙ©C‰øsy>!U²îüåñbÒ”²DfFñø‹«ä€‚JáÐvhŽpøß]#I?¯üA‡£ÇÐ¸pà$Jœ-)Í–Ô¦	/ò5Â+¿P«Âa› ÐD­ ´#jJÏièiÄ7¯xäU¨¯4þµ´º²œ·Ä2~´Zg2Xó0WèÊöU¢‰ºB•êÍŽ¼ò1_uœ†GûÒl4-^õb§Â+Åë˜ú¯»$;©W§G”Ö$àˆÒ@¸ª`vV¿Ì°MÁRï‡IRZpäõTkê¶éÌ±Ô£iŒ²jp’K•ï¡´î2Ž¹äZfè-äÛÀêÉe£´¢¢Vþ‚—JßŽº®£7¢VÖ:{Û.Ô2iõ1
{s¯âr­GÔÛ
ím»Ô¼¼aöŒâ^Íñ`khÍ‡+)Š2Ró’Ž°åQ0~Qñ³àe-ø°=Ýâ•ú*ÚÏïÈ?zàþ,ÇÔ‰ºÄ;·{lt+Nš5Ïª…2×ÉrFUÇÉ¥µN0Pê¬Ôvý8ä½´vªú.né\þ³²ï‹RíïÍØÏ¨Å:ža3nP{ì¶ÒÔ™õ#êeÛj¹ƒÎ¬¤¸bãèIRTŠ>1:qŒ âÀƒÀð‹Ò+Hˆ²lõ}¹p/f`7Ã“Ê©³xYc¾´EOó£S¨$Ù†»Ô«wÎ)ð<¼È@›ò}âk”™B$NÊr_w5ì‚¶°^ÙÉ­'Ñ¥ap¤î¥©`¬KÏ<mŠí¥¾usœÙÛ·(.>¬¤C™³3”ÛDžÈ^wá°žïÛ@»:Ë±4?·ä=SD.]Û£4M¹l¿!iCæsI4{7e]Ï…Kœw¿ŸæsÞPfB»b#÷EªìH›·´qÜ xI+Ï×„¢3¡¸!¢Æï@óù”E.
Yäù„<ÔrÉ—Z ›K¿Äö¤çó©ÜQmåÊó	‰`C"\3r,.^â{çó¥:G\¸‰k4Ÿ/.Î2ÂÖKt6HÜ„2as×s6:³¤FÇž³™¥½ÛgßÛÌbÓB$Ft³œ´«Ä[=ÑàÑ`vQL®gâ¬Â´“ ˜Â¸¦bÔÝXÐKFÝµy/×<«N9ßÛ!¹ØåIm,áé6³Â¶xd>e:±¹ÙŽðÓ˜!õ_zÕ¢ –²ˆñWò‡±üJÍ/â²(¾#ü¾™Ç"&ãÍ²}$'á|”þ†à|¿Ñ‰b*›HáÓ’¹Élã‹8w7ôÊÄòTE]ê‰íALiÚ?s¤ÿŒç›q	äNžå/GV×Òƒ[1/LÒ&óìðí
Þs&JÖ¼˜Hò8®FºZá÷ý˜Šë] øË%8}8›:":ã³|L§“ÝŸUJå¾_$ —Âß‘ÖŒîû\ÂæÄÎ×Ï]ùcaþ´_¼÷EþäóçÐ»ÜÜñå}þ]ôç¬/¯O	cØlìÓÁ—ž»‚¸åÏµ.éxtÞ0	-W3CÈðK¯^'Rêô‘[â®°ó9qéÚ!Å¦öñÓ#È^ûÜ84îäýþ+½½huÅ¤¯ò¾AˆÒG÷ÿi8&ì+Ö‡}µw6Êèoz®c‘å[ô(FÏYYí-\~6â]JŒh…ŽÓgF:ìÜ.Y÷|hCáB4wxº*Û}v£z_Ë—#>@”$™ùÈ~ÃÌ`Iò¡£…=lò§2³Nù{r"PÖ,»3f'ÚpåL"†ÝÑRáé¡›Té·°)Ú©XÑQvCIÑŽJê à qÅÃÌ)p‚;l!Q;Ñî*™m+2‰ƒ¢\¹W0Ëž¼J£8HAÃn)KÆtêìáÃ¿‘S+;~J(|wv	-Zojüƒ_¢æhÀ—€øq…‹mm_bZi$m ž¾kHËlå€,Ã‡ŸH?qáKÁy-ëB’¸Œ|H–WÚJ\Ö™Ý“ÝÁÒe†¢W^ÝX?M¡õ/q‡ÕÍX"õ¨ÐšñfT³0Ò¤ZùÚŒf~Ð
›Ñü“Žc*K	1—ƒ»JS‘ÅÉêå¹fIÅlµÙDÚÕ§^(Ž±ÀlµY§%7ÆF»aÝ³ï11-æ±…¦C+íÜ0Ž­,‚õþ1ÕPN­"|ZÁ±[ˆ}ŸÙq¥J`ç‡‡vë›+¡,hsd¤XÝLŠuŠê±å‹Ý»ÝO³D·¦¬øÖAó[”_Nénlôgðñ3šßÝ^½nƒze¸T’Š|²ÛŸŽÙÜBÉÑ†Nså„^÷øëââ|OžVW„WN¾%«f‰Ÿ2­
0²¹ÐŠBz+F\h©õ `“ä8Ó$‘| Èé `—ÏÇ—;„p@ÿR@Ntµ?™¿´Ð©áÆÚ™ùƒŸ IÝø:“mÚMðÄ·ù¹ ·ðùoáî¾-YAäÎN>)ñÓÛ:Â¡lny
–ž7¾3ÜböÝpID¯0í¶ñ¤‘#;®“›®,q—¡Æ¿hÅu·~Œæ\×ÂÁt_š‹§-Û]&á¸V€vp;ßG ú­íÒ/Jiãµá»|3óÓ´˜õû-”¸R'‹».f1»ä(gòÇšOg%À3â„›AH‹dŸÎÛENZ?Öd¿&ÍÅ~”(£øI_â¬‘þ²FIO .œ¥âç‹|}ž’+6ùD`šï7þZÏW@<ø˜õê¯E•½­ð5Ê—]à'ÏÀ}J´¦‡Jdd‡RwK$D)Éø×¬€:¾aÎRŠÑÚ¸+zì#d3|\®Ì²™áÞ0¢›ÎAãÕÑÕö!Ó£ÒÓPMºY¼¿ü©P$ºyõ±ÂL9nÌžrKH‡–êLN¦wk }_.£NšàOÌ«¨5ZqX-”¢åñÛ’)€2hOÍžº®i†h¦Úƒj¨5I¥Å’_¿Ý ïd*H³™úE7–€0S	 ‡SN®©¿Í“/c¾NžÿÉ ‡Àð ÈKLawô9pèI‡ò'•Î=¡hA>%C8ì¥ÌA9Âa©‡''[©Âãd(<L÷²b$©Ÿò§(ê:èSVúäÎ/´s/“5N	h±ëí(
§çC×åcS™ª*VÄqãñ55Ú{k-ˆ|ÅŒ‡
h§É1?«9x "AŽý¢š_0Ø~rmBþí¯/”‡ žk2WMSžJÊ€|åT€.Šp¨@K/¬ñ×ö Bö€µùúTn–·hRþ‰ kûUÝÙÖËªìÀ€Wãñ½åœe9‘ù“Ìv™ë‡¬»“'˜Û‡¬V-Óë²zýd$/fS‚ÄwI]
xdÉ\]XOùX7=ræ†êÔõðì)Þ®¶èÜ{…k{d™YsÉ2xÿ—aÌ·‡K–oã‡¬3c½TpÉ¼ê?d="…yúÕ(äíü!ëÆdÉëWkÚÏ›ªjQ¥³MÑ|Ý}¾è2úWoëVVNœ:~ãË>iÒ”ð÷þ¢¯ýÀKÞàCV‹fáºdv9ÿ½ÉjŽòvùõ’·³û¶ˆVÝ·Yom|È÷#¬ç­d6˜îÎ{¾íÎ[bžþ·’y£d>ÂQéÚð'e|éîº’æ™p“Ó“+é¹.r0ëEgâ¤àÏœl]Ê"¯ß“ƒÒ¿e¨žœ°þôe?_¿!ä¼0Ög¶ãçyþžÌ&ìù6g¾mÏæ­‘ý|ËšYç/êáü–u?joÄ~4ÅDc6‹°góæ²ŸoÄpcÏ÷Íc?ßó}¯ï~¾ÅAý…C½ïçª‘mÂ/ÌO7æ2¾ä"è|Ó›Ë~¾çûÖÈ~®ˆúVü~¾Îž¨¸5ò¶¢ý|×&ÓÛŒ.‚6!Äl˜ë"hAÌÆ/Âæó1ê‹pacZ„=Öx/ôEP>ÐlÌü5 :ÅÏ2mÂÞ!o«ÛÏWs·x·—M{€:ÑÕÛäyø÷ŸÂ¹B€D      A   #   xœ3äôÈ/QÈK-/†3JR‹K¹qÊÄèqqq Ce      C   
   xœ‹Ñãââ Å ©      E   ›
  xœÛŽ9†¯‡YèX‡ËžÄØ4t½	°ïÿ[ªmÇr¬ÿÓÄä‚•$RI‘,ï¶ÿ¢séô÷ùåÇûÛéÇÇë÷ÓóÇ÷—·óÛÏÓ?o'·ÿÙþ±ÿ>…‚HÎM2"DÞ^##RALÎy±=ÞyGS¡7£úÏ¯¿žæBío^ñýüí|îBBD¥pc¾üüúñþ÷ëÛ¿Ÿ¢ÖÂ‘
õúóü|úþ˜ËÆ˜Óç¯//Ÿž?öýïãüE@†"wÈ¿¾ýz>9ï÷/³»ƒ~=¿tß:hH÷Ð/¯oï=è†ôiýM6¶úñþñòñßSx,â>:P%|ñ* 
xœT@¾|'IOÇ¬CÎlÖ!Ëc:fí³¼LuÖµŸõYû²bóC	ë¯×¥$¬3,pçHIT%¸ú[%ØeÈÍVê2¤ê³)4ú¬Ï‹òb“v
™W—v‘™W…}	ŒÛ_Æ‹‰ª„èå9ÔUJPÄ£®jë²®²J°UZÄU2…0-c
ˆH¼®Þ@ù1Ãƒ)8¨A‚“5HóU~ÃÆb:¿2$Ê§¬(CYÔåò2Cªøú6ùvÂ^·¬|Î£©À/P‰nÓ§Ò%¿¡*Åy`½Få1É{¥®—¾W€ånß›CGà	êßí\^h$]Ù Z
Éa——åjÜq¹tkÜ òf´ÙÃã*éÚÑ–ZÈÁË2bò.ËˆÉ»joT´D¬€–Æï²Ü'®
‹,ù€Giò@ydÛx/OÚx™9/Gß,KrLòæªè~TŸê^˜±d©2žC·Í;™&$ºÅaÝ‰6±ZÇÍ)ÁL§û6à}‹ÏÄuÔ„˜da *ò4TørÉYO¬ c:«ãâ)Cêd"f=¨¨ž¨×³YåƒºßjáçÎ:j6Ntú‰j”Dc¨×£û¡¶§¢¸§êíJ±—Ü®t!æfkí—+B\%¸Q v}¢~S¢›2Q-©mw
<ê{lÔÚÖÃv ‘®YÖ«u3À`GÒ]c!u®#µí<uþ‚­3z58bÑ=Ý4±Eñ­¸ë…æFìuC)BEÏÞYÞæ ‡6g±A7Ér^¥P?
@ýV=ˆd yc¹õÉÉÇÛ!…ášn Kaã«RHO'Ýd4 U<ºEcz^Z­£1iz‹ðáï ô0yý†˜ýþ‹ƒf—‹M®kvÕW.zÕ^éçÑWÆÖÒKß„ÄW†v°Ú+ÜF©¯l/nÕW6Ë#¾ÒÇA^–@ÖÐ+ChÅG]Ÿ6ø+
^j|EUÖ§F-‰Ûk|å†äþ!GyRrV‘Þ[]ÚÜ¬Poi-¥ŽGœë‘ì›}¢Éîî–ñË¯—¿¾OþOä‘ßÝÚwŸž5rK_ùŠÈï]rqe*ùÓöGrË»ÒÈÅ•1rqÝ-¥W”#Wf7`om‹õœ:Qê QW—î>å÷)}Ùú	ÒÏ"½å_žÉ¿ëA®ú>Äò/Â°«?ïÙªzÚ<à×I!> rÖ¡vÖ¡zÖ¡Í9Ô‡î¾üïôùý×eY[Í<â•>*ôáJŸúôóíó—>}<¥½Ÿûôùf<aêÓ‡Sñ¥.á
á4]‡„)„S¼Ž)ú> ÝÌ9
kºÍáJŸûôþ·9GaÎÓí„)Ï7ôI˜Á6¢é˜@¼]ÓYÑöwE¬Ê˜®\(/èé*!	[í:¤X7§ÿ
q¯óüþs•<2òÄÈ—r,<#Ÿ÷ß•<º§äÅ/+ ìdðüœ=¿ì|ðü?}Ølÿk 6á€'Ì(Ã¢GÏž>?±ç'úüŒä?î5fÏŸ_~7ädô™Ž~f£_ybkŸèÚOL÷ÌL”g*ÊE÷“ç¯ðùå¬ ²SÈÁpÇ‡CT•/)ûî9àjUú¥±8žÑ—zFŸûä9ýÜ˜z8þŽgil§ô¡µ¢;ôðù¾±ê;ôp<Ž'4¶U‡¾± ;ôº<×²:=§ÈÊn  ¤) ^ª”76=oß 0¿ÔÑ¼(§§9Õ’Î¸ÒËÑju™žÁjC¢•¿ Á¿z}„bè%EcËV‰ˆ®ƒ‹Î'i¥Q/Ó­ñ¢kòr7älQ”æêAVG=×ëÄÇ·dué	) ÑI_éºômláÎYd¾ÝU·w¸€Øÿ˜ÌänêËAn2ÜÛ˜µ•5«÷íV
¬=Ýj$ie¯W3r/5«øúßêåà9âõÛ|+°Óë[ŒÓ<¿¸½‡U‹øé	¡gÚ™h•—‡úÑóé­oƒÌ‘®ŸQ…½É0®U&YÇÅä £^:T|Ð!PúvI_zÿïHˆÍýNß¤ÐSx¬¿	´Ô<­ñðº=kíJôsÊz®èL?”„-,õz©Uåˆ^ç\\ì0!—Í/ÐE=úúÈ\6]x·67zè’;HïõùV÷ËÁ´ÒûËï¾ƒ—a*È†®(cO'XÕí V€žch^v%aªrÐ;åT~,PgÝëª¦ˆž†jÍxx	C›)VzŸÐfTª¼Îó!hÖ¤[®ÖíèÂtÐíHoÚ`ê
–VxÚÂéêªšÅ“ê5Ö¥½O“é¯’žÉo º¬4³ÙÓjG{48}Ò¦á*9P"k:Zµ‹n
[¸TJL§Õ‰vÁ¸Å­õzÉ&M½~šôïiM8Ì ïVëøI&ÐØ.P³ÖžKX¸Fwª9èÅàÀ-Æà~ˆz“B‹ 15àóHÈ¶^A3tœÞ¤Ñ Ô]×¯n*`:}Sð\Ò{ º3^ß¢ÁÝ÷¨Ï —ÀV½¬3®tÑ0C;ªê‘KOÖ·’m>àeÔA<Ñ½i,ptúWõA™½>ªa¦ø8ß¸o¼lîLAˆÝ¬Þ† z`™;€^÷Í*"`¸m3n4é¥´†`ï([˜½£ ô$çÆÀÁz®é}' £ŽöŒ .Ýq3¢†2a—ÜmT <ƒ‡f®×Ã«va
£	ˆ&X£6ìÅî±åÌÒ¥öì*”¦ßXœ‘ÈQ8:–4zÓÙøø­µk J	¨Õì’k}¾xT¯TÑ;p©mGC[
&‰>à$Ð¬)‡	;ÜCdVªÛ×
‘îØÊ”ƒ.aó,°y„è@÷3è°‘’usÀêIé}ÉBãjz®ž]C{cƒó½r°æÜ»¶©CGW-y½dªÕècßÖ öAadx×L]Z@qdx¥êTPÞ„†g…¿ˆ¹‡@hN6¼i ”Ð’›Õ1šÚ²iáM# 7²z~Ñ}¦-âÓ%ÃŠä†äí‚¬o³dÈñ®ü
ÞêFú„‡Çæ·ÖP)¸ö²O=ÐÚ¶sêq+û0Ùp•9ÈÈHž¾fÈ‘’w1‘#R›Ó@
9²Çò0?÷8qíUwJæÈXo2—[>¦O
½Ãi^~¥iüÐ^Lm™‹¸ý“l5æÛž»jCµ6°¡öpí•ÚDíó;t€ÈÑŒlýRôJeýr¾ÆiNnÐ?pé*ˆÏ:PA÷¤òÛYƒèªÈÝžÏÒ‘aúoé\éQï6”^¼=ŸÒÃù&8þLùåg‚ò3¡ôq¿_|«ô¶ÕðÉ]o
ôoº˜€©™~ é_Ä3 M× å sT¢*«M^õ7 +|Ú6Y¿¦².ÈðK.A@^ä|Ä†?C×O‘U÷o?v]µÙ%èùÜg–ñDv……=?@]Ø ²R—Ðö÷zvß»†±ñ]TÃ™7?®NO[Ü&Šq¹Df´ÙÁ¼»¢"Ž‹…çÝl®ô»*[uúXé—^·œÒ®å˜ö8Žàžw¨iø¿>öú¸ÇÇ|GÄýƒ †Ø¡m³¬{I—˜3Ü5EM?}ê«ø'½WÕl‰¨–$[Á0‹ÏíXËÍäÝð¾¼¾½?ociÐ†ß:´QM;To³œ2²á¹Œl”š2ÑÝÃ†™J‰6€É´Æ1Óô÷LÓŽ³ž½j6 ýRƒ^ÝbÌžJz!½}kƒ|z3Q@ö„YûôsCza\µöi‘@Ò‹*ãôT?PYÒ«æq‰1§¤Ð+À¤‹+v°a¦¦_» Á¼&þù™¡¸þ¾`TÒÎgýëuÆ*êzõ–iAúA=½Ñ–1‡¢
¨'HYø–J°žöc Òb›:r‚îÄ¿»}±¥mgÀ×
@iºŒ€FÞô>}@[fú!Ã¬È°ô|oÐ@šþ•6P«KïÇc =ÔMœª ð'BõŽ Ÿ¦¦>2ýfcÖ¿ÙhËJeI/´Iãk›Þ(žÜúw¦m¹èÆ …™öÖáÉÀÒ+…mötÓ.Xºà7Z¨ØºHË¨§W‡ÛzÑ¦Ý"²î¼ÚÃv’Áëùék"_D-Nè&yê8¢l#S{>½:2û†ãªÎÄ_4 öÑ‘A4˜¿JÁXx3
'é¥±OÁy·òÏ²™hà+sàWÇ="ro wØí	»ÿù×§OŸþ‡<àe      F      xœ3âôMLNL*Ê74ä45æ44€d&±¥%›ZpZ˜X iNCNhj
"€˜Ëa,æÂÄ‘	Üf[špºg¦'RÛ\Î ÏàGÁ–@`nih erU™CƒÁÂÜŒÓÔÒœÓÂÔ‘1z\\\ ú%8e      H   
   xœ‹Ñãââ Å ©      I   
   xœ‹Ñãââ Å ©      J   
   xœ‹Ñãââ Å ©      K   
   xœ‹Ñãââ Å ©      L   
   xœ‹Ñãââ Å ©      N   
   xœ‹Ñãââ Å ©      O   
   xœ‹Ñãââ Å ©      Q   
   xœ‹Ñãââ Å ©      R   
   xœ‹Ñãââ Å ©      S   
   xœ‹Ñãââ Å ©      T   
   xœ‹Ñãââ Å ©      U   
   xœ‹Ñãââ Å ©      V   ­  xœu•[Žc!D¿µŒZ~a`/³“Öì}…:	q+ÒýpÛÇ„I™™Öï›ÿìß¿‡­àVd}ž’’¯@ûÑŸ’!:×Çß%§¾÷Úáx×Vè>h¼kA²Ãë:b'±¶ÎªV’}Nóv’xU'ÉXñÎ•*?·™\ÉBº(º’"]ƒíª“ØÉGBJÝÉvýeÖz#Û¹©ÖûÇ)‰—z'TUž]yÑ5TÝ{©OjX?G¥k¶xéÍK](öÂ†É„*u@6¼Ôm7;Oi£ÔÆu«õ$n×wh½ ¥‰²  [šä1þÅ‘øÉaär;A=í=×¼–!ô!1Ÿ¥C2G„z¡h‰"&H0}8,a†c²–Oœ±VÜJG‰Sr+/A†\´+ÞŽûñè‰Ó™õ¥c$Ö.£—ŽIŽ›Ú š·Ã*TÝ-féjØÃ÷ôó™õ‡&Þ‚·%¤töZ:òAÄÑ›•ŽF½íŽiøp
ÔthCM/>¼'è{g›œòÁÙvUíŸO0Fîö´õÿ‘<÷‰¬ßÕ¿_Çã?sŠ/#      W   
   xœ‹Ñãââ Å ©      X   
   xœ‹Ñãââ Å ©      Y   %   xœ3â4â44×50# ‚qMuŒuM-9
¹bô¸¸¸ ’£È      Z   .   xœ31ä4´0å4ä212,€ mi°4ç4†ÈXB–@FŒ þn      [   ¯   xœ}‘Ù
!D¿M1‘Œq/é¿ŽplÖÀFâ=fd2˜€0 ¨&ªØPB»¤­^«ßc ÒMEíÆT•Á‡£4Ô½í6´‹MÃ*·ÎìÐå3Y¤,c€Å”ºåej›r‡N§­.OÈ‘ÕåÏ þ¨m…{Ú¯íÅõLËÊüc”ößØá¢|–ÀÑ¨Q­Ç—Dž¬Ç‹µ³½Ø÷+¥ô=îTu      ]      xœ}I².©Žæø¼Å”Ñ#Íë
r’e¦YšÕþ×Q À‘	ÿ#Î nœïâ @=R.€¾ÂŸw®8]Hý?éŸ¿ù×ÿùç¿þ×¿ýçÿþ¹?÷\0´ºàBtÎ_@ÈÜ~×17äø|ê¿,7dmÿ«#cÿe8^ž¡ÿ²
\.È°ß×îìµ×þ»l?Á•ðW\lcu`áCú>$Ãø©!}‹>1 Æ‰*Ÿqú´ÔoyÇÇ‰EÅxñ­¬b&©|'T<&=¨Ô§ÉöHÿØ di3öç8“Å8UÅ”=N²Æ©b}a ˆ¨åâ£¶øàÄ±S
òh¢Š	ãÕ……(TÌ 4ô	Wãt„Ah¤	
EÌG=‰¡rLÖç|>A§Ï‹ÐY#ttTŒE]}£®,Fù±¤},ÍõõÇ>\û£CŸ}É 8Dèà°Á¾Àiƒì\Ø4ò6Ü8³†¯id¶ÀP>À…+§Fç€˜Q£â˜Q#È‘ñ
.XŸÕ-]
Á/n+³K‘RÞd('ÍùÒ>kØs
'VŒ›ó[6]±œ[†X/Ø‚ä?ùB0Ï á&>7;<BÆ níÃ_¶¡VB~om­Ž?}Þè÷¢*m&þBªš£8NßG»«Ø.Ùµ[6Á ö æ¸àšð—JXk$è’a#ÿùÿý/ÿþïÿü¿˜¸„‘·ùÙ×»’Yûzò[É¬u,è%Æ	øAÉ„q ~P2áÙÿ/%&áûçc8M½äx¹M®AsÓ$-„ 0š&!>7ÇRÕ $A1Måƒ°ïª¥ïBëÒd1DÇç¬jFýž³¡BbÎ*}büE¥sL|gUÍbá_Õz V±.}\¼ÉÖC 9	Ò4#H’Bš®)ˆÕ«³NQPQÕãVÒ]ðAð(vñIú€>ÀyßZ¶ÊÞÎÝˆ}­–8_0ìÔ7R’äÓÔü‚R­69YÁ(tk“7BÊü©&¤*§¦™_A‚4í"ðÃÖÂvbl$¶ù¾ÙòM„wÚºœ`êéÏk-Öæ5HÌB†ä¿z®¾ˆQ²ö!.C[+
l¤¼@àÒÐ{¦éœØÅ±ÜŠY¬‚„E>ßŽSÈ4Êu êÒº¢Ñß	ººÐßRº€oÈoÉ	•Ûu‰Lå x= r#ÚCþƒ’çH©‚äËÅàN‰Ð´\‹–¸BÞL~Xcæ“Dø3™€ÐâK8¹FÅ?®´]±]Â·…1íæ y×¬„mã	‰agâ„$‚°ö†`7ˆdÉjx´°O<W4-`x×pÉO¿ß>Ç×£\Ã„dN, s¨ò¬µí§³—PÙ|±§„›<«8‡‹výlxoáüØ‹‡s£$±YÀM#
+ì†o»Þß*4”Á2~Ðô¡kúú¡ÅÄµ–ÇŠ:1@£1!úŠèžELûî@ÎÈìº‘õiÎQ}w4BZ;³÷ë7{oàÂÀÞuj\ÀÈGv÷‘» Ýà@*†
örd>ç!êlpÓ þlƒ9’£ÁK:ûûœ#i6¸Jj„+8ØÌÅ4î›å’˜àÃ3×]zœï£E0ÝÎçND
ò¢Éa¨n_B¢I_zC L“}#hùárŸ±Ûe
q‘|Ø•«	Ñ¯<v£ÂåÊcW÷â"=1²]¤'vYÓ 7éÊ>¼å
éæDc†·%wµ¾AnÓí~Ú¹M7!AnÓí\ˆ×évFÒ!ž>Ó&­+qØ¯ØJpagwsé–Å9‰…ifvçfÃÜ<Øo1[½f«b®£y;0Bßâ%˜Qì—Š)‚Ôª5Å?ô±¼XÂ^»a§c‰|]ªGË ó-Æƒ¥ð9«&(–*Ö¥b]ê^T'æ¬Ò§>gÑöv`
¤y;°F	Òlb¬I‚4Ãk– ÍG˜›/ƒ;Ýf:ciƒwpÇ—
®Ÿ#ÃïHF6ç	²ÀaƒÃ×4-pÇk,0›sÔxÇkFPé—°ÏMjR¿Y±†…ˆ)‹ã«²ãÂÆÒØq¡3ö\”HI‡ý;®£r&ØŒWâ¹çÌ"¬Ãg*Õ˜Æ³…ýñ£êÅ…À.hl¬jë5§†ãbÇ76£Ú,RÀ˜f»=.ÊûÀúpLìÃíË–UU²àÖQ¸Ü€ BYT._üŒ³íÞö}!®ø×Ô¿¿\›­ó2’ˆ&|ß›ˆ<÷}à‚\y}¼¸w±ÛÞkiÔŒ¾1d~ž
Ú}Z¹é®ÚÇ9§nä&‡›¬<óCÀØ“â¦f0¥H“qÆOí`â;Û€YœÂl~¸ð»mŸÖ,v¦‹€Š÷³¸©/Þ¾ÈÏXð†m_ÜT&.˜¤™ÊÃºOÙÄÉ{lùw£×.ysK
ß’TÌ/4ŠPmÂp­Â'‡\ƒ³r´Š«\Cë®EÇ5]ŸªN˜fü	#;@´¿Ž\.–bs#;$™Ù>s#{F„
p#Mß€|U}µø5}]
÷Ò£Ìí¬\)íÑpb;«±M
çùx¡˜¸ Ž‡3qü˜w7……ã<ÜÛb
„¥WÑÄ	¹k¯cêuÞ†Æˆå·m¸I—85Ðz„§&2˜ç Ð—:ÔüV–˜¤a¸`Ù9ÈéßC€Žë)®Øãá:À©bxkæò3š|Ë;ÎÐûqÖ7Ô»m¶½Bë yÇ­Â€C÷Ž3ôX,æÝsc‡òiÝ0ïøŽÄliŽ~j½¦gysþ@f …ãW"FsG¼T‘³Å¤¼÷âÌXÚ‚÷Ÿré3ô\ïñÙºÜÞ¯˜¤öB·µ÷Øíµšgk*¤SÆ6µÇÂq&ÕD†‰CqVÍù/l3c< Ÿ
AŠ‰Ž¶7_} /	)nƒâCwÜÜ¯ÅÝ5O^H|VªOyüŠ@•á$_¨&DsïÑÑäUiQ#v-¸êˆâ¤ÓlÊ¯j[“£#à”g‘«mU1G&.‰ñÐÂUÉŸc5?\°™&úˆ^Xag!Áƒy9„åÀrH”VØ&ùá(E¸yZ§‰½B¯—‹ÓÐÎ†æ.^Xâ¡ZÝXº)c¼QÏ$(¡ÚJš-B"œyŸ"r;Ò
6¿œ'ó,€‘ê@z³¾:ÛlìMž.76Y˜sNá€…šf6S÷ŒV¶Ÿî›¹Á<‰›~)Y˜O\*ÅjRq…bš
GÞ[­ó3–A˜!—t@€ûBò0?¾²¨pÄ÷>ƒÙÅç¯Sò|_C–«ûLiÈjýL©éÉ„üLÓiÈaÿ±`‰|Œ¿{È½ç8RÉrß0Œâv/Á…‡ØFØ¦aâƒ1B
#f®…&‹ù(á„Ü4RovgpU^ÿ<gÃˆ#µó3&ô•¯×€"L~ÛÂàö™4b8%x'æ¯Â{At%®Ò0A,#Ÿk˜$®¦ºÁ3oâk˜Â¿¥Å¦¦
šëkñ-íàúüî#‘å½ya©Ç‘nmÞÊÊ¸¨œ
ä%HQ9(JÎ*3ßcU°3$tó,‘Þp4ä7§£|Û†üæt!Eü›Ó…4´ñON×Tò Ur>Á£8O§7¿„$UÕ>‹Ä•Ë{ŒBïp ¨Çê
M‚å™N£¸¾>£ìmŠªf'7zp`áŠÄ¡›BoÙcÞ€‘Î^~8[‘¼iå‡³aPñûlE²Êg+’-P~¢‘¼tå)q¬HÄn}§BšqB…Ž\?ÁyƒW8Ö×
^áXŒ>¦‘[à
ÇÚ`¶ÀŽµÁl+;Áï·c
\ÙŽÄjœØä@ÀŒrX1îS")ûÀ’õQï,Y°ÀaÑ¸Mä¯ß°¬gÔ4X+5aY¬Ô"ÉÝ=šž‹Ý`bšŽfÀÄ.ÄjÁä.X° È[-ºAÞbÌ-ÂØÓÏ—}%V|ØÚõµ`C²(†ÉtVôÅ29±#aæ`zõrqNWr§§I¿°!NOÖ·$Ñ1èUgõ9fßò11èÇ¨ó*|ë]
õ	zuz¹ƒBå³}‚^äÈp£Ùç8qÓ«u›‚¸éÅp«¤ nz6G“7Ýb}Aò[ón"©É¼éÑqX±ØKôf1«8Ì[+\ÜwÙkÀ2-[‰…Ã,Õ*%±Òd1«$–-‚¤(Vj1ù”ÄGÍ¹‰•snb¥É¢[1šµõIœSNe/6Ë"HI&LÄ¼293Õ1xk	¹pX4?ZÅhy‹ã°`)Ås˜¹%
˜¥{”$æf"Ír‚t7Œãéžm†‚ Ö¬‚nÑZÂ4¿vâŒt3oVt‹y§XßÙ5¬
˜ùQà0oíÂÔdÌ"ï´¹v&KLÛ¹ÀòëÏhMpÈÜ…).WòÅÉÑ	˜uO§-6aÙš®ƒ™pkfìivÂTTÝ¨yêr7ivâ²¨É<­››G2;Îou^öN`4^ö‚˜ª·.{i¤ë˜(è£yâò´enÏì3;ŸÖ·¸äÒ½‡yš07ïaö Ö¥Ï—nj»Ÿò2]n¾¥‚ØyuF!Ê4a^ŠâÍ÷˜ƒ¤£z>„ò§»âs ±¯Ú¬Ótâ¬8}yì’÷“é6\‘s§½“nØ„B¹¦lÏeçÄ÷xÎ­ñÈÅÅ¾}`&qÓ™ù”¨0žzê°ÄiŒø~^R¬BŸÙ³ôGªnŠ|¼¸^ŽOXØü`ã‰MBëvw¬˜ot·9d¡
»z7K}8Ýèßz]ÿl×ºÃ*ã¡9¸x[[1®¿[¥&çoóvô’épÅ¢ÀÖv:I÷k†Ç,=^>$Òê:‡iIO­!¤Û¸Ó¡9¯Õ=Ø|˜Æ¬­üƒ—†ö´!ð¨àÃbF´ž±Ó¥‚ÜE°ùªàì™Éð~õÙÀQr¦Ê¹âNìð(Á{ñt>DaI±Ó^:¡k“Ý
84ßxIvžSÍ³K¤P->àð"D|ïG
,^§Û
5múCqÒÈîü¡ähû6QGd™ÚïQGÞÊŽ*ñÎJò5p,W0Ê‘¯9àéõÙ]Ážƒ}½ä€×‘R’‰­‚í?k­ìöŠµÖ@æ1þŒ«ÌÐŠˆÕ@&æEÄr|þûØ24("Ö™?,ž¬Ò§ŽÅª´åðCa¼F¥gÌGo/ïÕ_ëx¡x/ÞÙ@U‚5ºŽç‹÷¢›=9‹ÏòFÕ‘·ß[\y€ÌÈl…¦j ¾VÌ©Á*‡áŸJ¹fl4‹Ãr˜áŸ­X‚572°ñÃ?[Ó-çJ+žCçÍ•â ïN
6`“¼;ÓÀ
Šì÷>¬òÉU#õ°    Fç9åÈÌÐp¹sÂNåoF”»cµA¿QîNÓ†üfD9Ï3¢Ü%]C~3¢ÜùuC~3¢ÜeâXüÓÈ)1è-:T3x-Fbc	4¿5`óÌÆÓš+pà¸Ú=å5øfÂ‰²PmE…°Ÿ
jCVB~†Ÿ#rç×¹aè¾é†|6éCZä4ŽÈwX®ÒK5ø.áÙ$ç·ÜLÄl#Ž‹ù•q×”»¡$üp’B*z=Ÿâ?ÔümÈ@È´„4ÄÛ÷		iÈ¸ïÈøþ¡âp#hfý~ãª¸qôz²?ó“ÛMròÊ…¿þØM»rQ\¹þfâ’ÅÍË'“¯ÐýÀä…éoÒú÷0G	b*Ç.Þ1öÖ£«jšsÃyÎZ£ñ²®á8cõ`<Äj8ÎVc²Òã0ó…ã‰ZÃ±häï7 0ûŸ¬/#Ÿ¢Mš¸,±^w6\8#ß¾á
ÇYO%šPL(ûYW©ýÛsDøIíÚ[IKoøbf½6û<XŸ/w&MÈÀq2š%	šf›¥f«øukH¶ýÉ”S\ìîžøZKœ^fŠ5õ¸åÈ8nðÎ#ðQûªÄ¼Á¾À•M£|€ƒ¸g!êUj!êÑÈ
‰FÿƒFÖ«Bvä7Ó/y|þ[#+=`Œþ¬ô˜1ú4²Ò}èö¥Ž¯sÚwU‡=´ïzòÏ]½€3›C7€õ’±
lYV’Iƒ!‡AØZ >›Ù¥„6­Ô-£ÏîfsR»Œ=–”ªÔ
ƒmŸ(©ÔSfOÝHk¨ÔPy±LövyŠŸY7aÀ*Áö“püHiÐJÍgæŒ@h¥Æ2Œ^Jð©Rc™5%=Z©¯»J «R_†Q¡µ7^à{|¹¨XùÌcÓyªªEbƒ.úfÉžA¯Ú5®aEÝ £D6+5®á'_s¤PSšM9-ÔZ©ÁH“[Ôá…ƒ4P®ÈÕÉá#é®hÅÞ*NØF+5¨L ûÍò™ /=¡„À…ÿò}œbÅW¦Dõº#}Ì©pä1¦ÔU RWÏñ²[ô9äºÖÔˆmÉùÖ¡Rëv•Ã	¡æZ›)ÌP†÷ÝûeaíåÐ×pwc¨äqÑ¾
—’Çµý6†¨™3iëub°³RS“„‘_0OjTJù"BcÁ%‰‹K.cL-‡:¸éÁÑY9Œê&„á%„š
uè÷Aè‰cÐƒg¼‘™!%#z#+!?
yê‚á]©ö±¾†ìñ	ß¾Úc
ø­}Q?%?h_5
²k_Ôv	ÃÚWMÙ?´¯šª`ÿ–/µ–È¾V} ÆÊÛ§Dˆ®R'¶ç`Éó,¨Ž†³·fÏv±¿§5`‚à`8{©™Í8ääÅ5r¸*µ>z(h:Ó©ëÑ†s©…ÃŒW#•z±Z{‘®×\0¶ÌñÑŒÇ%
æÅÎš 0˜õú¡R3¬=Z2aYŒf¤>š¥qSÿç
u‘bÀ€ÃœžkY©ÓÐ>Ihíiä¥á:ÛR¸o´=Íïpu¥–LÏ€Hyç€Ü¶ðF5ÜJžïŽ‚Góº†$Æ¤ïæýÝf€é){@a¤ÉçB*¿±F™†J­’6Ì<Ÿ¹`0o"8vT‚ÉMÀóKa¤öWjôÀ¼ya§©7]F~w¥Þ%{¥h~4syeÅ«*As4!Ptæ3ù! ;$ÆiGÇ‰8íñýL¨ý°q°>ê_<ä<§×
ÐýW›\5&WÙä*ŸÜñÞ©aiVÎèyÕ0¸]Ñßì“~4ÈÎ3Gˆ _:˜Lƒ~8¢Ç…<Œû£†C\ÌÎØ~pòh‡	œ¸ùÆ«“ƒ=ùìôÉ{·1Å©ç<£Øèp©oZê;éÍ€¥çHF§Öi˜,ô‡ž$£û°Ás™ß½Oúá…iU°AðÜû¬$ ˜¶õ·„i·Ü^WFx°D!LÃp²A‹áSç¶A»8Sf
ý…~³–ÊÔL²l}°ãrsåiƒÐ¥¡{)¯àu¥êv=7½¡Ž›TkeAãJn¼ø‹F½©0þ`…Q;Œ?XaÔ†êAÞ¬0jB…ñ;øIñ0~›kÔãæ5ÉÃøm®Q§<ŒßæµËkÀosšæaüÁ\£Æ`0×¨ÉÆÌ5jµ‡ñs-JoÝl,ÒDcIÒó@†X‘¶Àë.
p""H8µˆ%¸\ÌÚ­ªÀåwÒ\µà¦¿ëâªm™+¢¸jÁÍàÅUnÆÿ.®Ú†)£¸jÁ™@¡¯kç.^Rp}/éÐX
†:ÎŸ]Þµ %ïuiŽTp3²vy³Tßœ­KŸ³ ³±®²‘÷ ·r1¸¤VLN‚ÔIœWí=JÃ±g*fâÊåíKÃ$9!¯MÈ?K[	ÆÃKzA3!\ÀM‡ðÜ¼oÐÂÏo¾BQLsÖÐ±3It'?wE)5Wp3ûìU£Ä Ïì"ÑŒÂ6,ÀïÔhp3¹ìUÐÄ³†úŽ(˜Öénºm_Všù”L'å‰UëEE§Nb<š_§©^iê}²H¹ÒKM	é	T©¿K•jÇï²y@µÚñ‡²y@EØñ‡jx@eØñ‡jx@Îtü¡P)vü¡P!Sü¡PÙvÌ?m9F~(¥T<(¥T>(¥Tø(¥Tú*¥Ežü™È¹Q~"y.ô:¯s‡ãº}ŸdrJ¨uVÞÀ@À¶¨ëu¨yy™ø¥ÕU!Çj\Õ"Çj\U#Çj\Õ#Çj\U$ÇòÃ¦S…îMöj”e*¼ÝG|‰Ž^YôT}ûã8x~@U…•ª/Ïki)¬Tx™]M‘ Gl}³ãX…âªàÍÎ¶O;Ãìõ²¨Pûƒ}žâèX?Ù£|”Û¸•ít/ÄnB©ø?›‚o Ôw )¹TYž/LÌàØî¸EêèpRÞ%†AãG‰ÝÐ;òÊè>ÐC5<Þ@éX_6<ê”†¥N%˜¾B€Êþ¢Z]ö@z1×ËQ‘tÌ‡æ×Õx,Vè©:¶¬;ÖVëJ›öé‰©b©#þð@¨Hx¯üò•$ T­{Þõ- ¸ÃIj™sZÝ>Ÿøòï§ÔÇÆrµ&ñ½Êo’:<gÐƒ8Úoís&S‚'õÿp1PùI&ËJ§êñLŸÐ¬'*zÎ0š•NÏûébb¢;ÒÁ÷jRçGq&TÎPžtŒß\½*WaOl(öÄb"I³¥©Ò9;¦úÄ27hL¬ìÝ1üô–ô¡*òÉÞ’îmRô„”Ý[Í ¦—£Œò*RØÔc+@v—2ààcò)í•†O°PmU×OEl¥¾Ò*¶R=ü	…v¡Ž“Ý^é´ÅíÉg/¶I%oB¨®ª>ÍAšS‡jÜñk=ž zÑÍÒ|:$8HóéPvÒü,~Îvìü²˜_±o¢Å±ÕP$ø%‹_¡Hc@vºõ øÂ4J=s aÊ>þó£Lw–ŒJW¿Á¯ëòû6pØg ÆÈî<s5²Wº²[ê>?Ë˜`»ú€…qçô5 3E^{x‚ÝÉ×	RÀlÃ½q‚ î©úÏ¯óµ×·³iXÆ¾šè…§E6„+HÇDá]Q9&QÅ<Â£üZ*EpNø|4îLýðÚ_ ¨wÀöóèö¡ËÒ²yº$‰À%Pƒe…ŒÃ­pzØ˜q^OLÉ3Š‚©lœ¬c*sFc>•ŒoUd˜¢b¨w^ËæµEÀkù}ÌJ³j=€×ž¼8‹ª ¤ÖÃcj@ê=ÀAš ¤æ¤	·0-Å›§îxí¼ aY§7!¦¿bE¥3ÐK®G3Y%xt³
„2ã
š˜ÝÄíìŠŽ+Šé:*÷ãôrú2[¨×»Óg:;P§äÝ"NH˜¦ÚëYïbÃ­*bÅaZAëZkäÓ
zSŒëPï~!À°~Î÷€]²hNsè”ÑŒaŒ.S‡i—[²ÚÌBÌlÉø5`a3´–\Ùå’ßï!Lãg1B}@d–§Dvòh&¿dñ,cÀGaô=V÷a´‡«PóXqOØÕ_¦‚?½ŠÁ(•Ðp•Ù:ýµ…ãÜÉY­¹ ÇÇ32µÌ/«a¥8¸È?zÊÐãßgµ½¸šôF~Såi•¦ 9YHÜªTa³W#3¨&Ñ^FÐS¢Š'l`ÔªH°Firßì{Åé1¦2"àÝæéGt9Lû~ew3ìá¶¢JOïÿöÔ‹©ÖÃ–+–‚ÄDÐQ¨2Âƒ¥.6¶>ÌÌÊ„„PùÙH³xV¿Úïì5 ‡×ûÏ‚g†øËö¾(*Ê´Åjß»œ³vËªãç©[(Ui^T‹k,<Z™¢,æÂ0ÞÀàÆœ¾Ç)½‹4L
{#˜È0``úœë/ñË@†^ý!†H ò;âG…bò;âGOò;âG• ò;âGÅ Æâ?"~TýèAF«5$Ž³ºO]Ú¸lI•Hö`eú¡…óâ»öxA|×h°Ôp‘ãŠQ›£á’Ï’fÑe±£&HÃñ]{½b?Ìltb?²õ]ª}‰õ‡¨õ¥Ÿ·ài	0öä;zCEØò;"DuÉözv¨«œy*NÆh™¯Xq.v+ÏF¸bÅùØ^ÅŠ3Âå†‚ç$¥¶>wí+âê<Vß!¯èÄ
.æ‰öbÇ¬š\
ç×
Vûò†“;eÞÙxÉæ>qœ·×‘9ÎÙë(gs_ÎäXžsó‘ãÐœ_pbæüßþ0ÐÂŽË&'
|?zj'ö#™5ˆýˆ–¤‰Aì‡³¿+öÃ–HAî‡M?ûkTŽƒÅ~xóÜG¹æw£Ødžƒ(îG1éÅ~D{~b?lÉÅ~X­ä|AlßìñÄ~\ÆûáMú%'î‘yÒ#]ü|5mRáh9Ð]€‰»Œ±€YŽhnr*|1Þæ–©ŠO›î€˜€hk1¡˜c1Hvh~:{	4é˜ƒštÌbgº¨²€I¬:˜§1¿vÆ^5ßJ¬±€|g|WÓ, Üûôd±3ý–,N|ÚÖ¾‹Ü™hƒÑæ²%Š[hïLw¦G„, ÜoîLwÆ¬óäÕàs4w¦€$¸yzŠØo¼z©Ï™÷ºF	4SÓŽd3s1Ë°ÞîHˆÌ ðö)›FÂ~mmáüƒóÔ‹ÊÂ>ž7I#žî$³p‰WL…d:ÖxæAœ®ý\ÑÀ¡ Ø8®8ë!Ñ(Ì=¼‘Ï_ÓEažèI6Q¸ô$›¸Ü	·œ8}	·˜qš~„[ì9MßÀ    -—œ´~µ@^ròŠ¨¼ä¸ºd
TFª§iàß‚üÉqÕGOîJ^šàêâ}”Ó«Ôø“3ˆi¢'ßãö2‘ü‹RZ6y9 „Óçu„K|{²# ¸§‰C_¦sÄÈy‰“ñÄI\¿OE¶á„TáIÊ(>ˆ-ŠdÞ—ŽY’½$ÜkâiZƒgÂ‰ž¦ÞûVÑÁqƒEÜJç
BÌˆ|8âS`ñ8
ÙE4POGÄNy8·"rNÁ\ñê·#ÇºtÅ&ŽMþŠÍlš,¯b…—÷íÈïB0:!ã”G}tðÄÛƒ¹ÑH/¥Ø`4ÑDÆqò‰¼§.²FU¼fæªx—)ŠŽ*CÎn•¾pv*ŽwÎžƒÀ¨œºŸàïvVxgÿÅ	Œ&ÔGsQ¼³öÑkm‡H»ÇÊtNZ¸$:[XšZÚÉ§Ó×Â‰†¦úœfÅøí”µp¢¥†©e§Ù,åËiŸfIû5žùÝÙ$fœÛšf‹˜åš±¿›9Îtq¦Ùf¹\,Õ~t-ÅOWãh[ŠŸ®ÆÑ·?]ˆIôj‰¦Çe48}Æ3]—£!~ºòF¯4üt5ŽŽ©øéBL èlºüT±{~‚Î¦‹. ³}NQÐÙ¾G²û‹éRK²ý‹ÕDFƒU|R>L:Ï>1KLÚãeŽóöx…ã¢½`ŒÔ›cBÁ”ÑÂ–”ÈRê,œç8Óç–g•û…³øËh8‡¬^…K[H¶©?:Þ>­qL>4ºÞ>8Ó5=º—?b¿)/§6{síxêÔhê™2Ú—ãËˆ”otGËKdFí©¯T!ýJÜŸ|÷€Ñ»?mòÑ›™-bà<Ÿž7}{£ÿî£Ù'Ê‹3}£.~ú4F]üô‘Œ>ºgq–ÑKYÉ<œÀÙî-á¡\mçÈè{—áiFßã4ãbq€AØvåŠÑÕ#…¶·38°À½?;‰·º£šÄhM‰oõ>útäÛ¦ÄU)jÔ~êå\ÚuoÁ©—ç* ñ¯œw(…¥a´¤Ýs‰Ê\@h.³í\ÙûÎÏÏ‚ÉÅGwed®÷h±÷pÌè²ü ípÌhiü í0Âh·Ì>mÞÏ hGFÎ
4uÙ_V‡=b@S+ÏQ²_[ŒÄ*æ.³på|š_'l {2‘LR3·¿ì)Èò#ï"ËŽKÅ((yvº×ˆ…<ÛG}d°æÙ˜tŽæ,øÕòeÚ^ÑcQjQ¯´§	go*›å®à¢·`¥¯´»ú²$;i(ô”Ü1
 ·µÔ?VR§»|µ{6éÕËeTßÙºí}; síÊÃ†á¨ñÛ°¢7ÔÎßøî3Ó°(°Oá%“öA²ò‚3Ù´kŸÔ’pWÿXT3:’0\ß%k<ß®:†ëi‚zÏ–vŽ}¸ó~cÀÙ¶heY¦?êsž·Ùùl©:Áè<™õômÄÖ7\Eq#J»Ä7Î•8¾«Kd÷Ú4/³J–-äQŸ½XwÅnÖ Ð›¤ƒ	ÚS¹õIŒ›7<J
ŒÔÃ|jH´Ý¡xQC´}–’•|OýËØŽZb”Ú—±
°¤h	N9K6–Ù@pæò;ëî”Äï¬7¥N™wq®×Le+•ój;BZjâ'ØôóPŸ¥ý]“W”ZùxÁïÕh×2Š¼b¦þC™žžŠÞÔAÊìð;Åˆ™m\Ðqœé8*óÆ®ä¦ÝV0ðÉö‡“ ´y²°0–âMÍ‡
íïšvVuBº›ê5	=:9Yzfþ
©®ñÑÄFwøçÎ3c«žÆVq|åý•	 ¼ô‹±t'.K
¹(|œÚ4î{}fcD8ÑÉí“Âð©#Ò£-TG¢­6öŽPÈ¤ µÍœ2„‹õ^"áì åÆN
íp>å¡X×ÛÌÈ—Ó_ÊeR;O‰(Ne/çÞî ¦üU¡}?¨” ˆmêÜ×ÓVm<¥	ü¨|¼Däw6÷ývêˆ‰K
zißt:í`$~{µ3Cc(©
 ˜À²Ñt·Ô¢ì-B;£äW?j¤¿N^âoI%y™W|žµþ¾ÛÚÇ]c¶9—nøjHÁ®º8Ï†dæ¢µ¼V®£˜gS…1£úñàùÉhÜ1K´ø4IÇn¹ÆâN‹äteúõøè}ØKäÐžÁ“¡fõe1hãnt<4z.yúW‹½Eì%Šž=‘—«ñáx–„*Y€W{¿»|5½êàY¤ ¯tnÒÀìºöÃ.8u/nÐ3#ý¥Z‰\Ö÷ª9‡]0p™Ë‰‘…­_‹ÊÍóË€•sÖ^éÄÂ	Ã»[.M=¬…“¦
oBHt[Øù—{&›Akä´îñ[ýÃÕ	Ê4þgŒ·lÄuh«¹’*€Ù¢auÜ:õ¦ÆIm#·	fúÇªÐìtÜê…âgç›V¡3Øï¸ê2eæ£w­(LjE4–ujk±–·‹Ú=îñÌ`Bõ‚Èö‚cÜë’·Zƒ—@óË‹s_ªÔÉ8Ó¶lê\¸û®£yìoÕÆêdBgE¤³[P¿5 8}À)yx’Ôe@F£¦U]Ì<¸WE"u@ÆŸšVÔèï°Þ,âºuO†¥ ƒP²Áa
¥6Á/õ…©/ßš'«Õxº?<®uixÌ²Þ°Ÿ,UÓ–JEàÌkš¸€ê®BÃ; I\e¼¡ÑO-tÅü²e#ÔÊÃ¾ê€Ç3œl£µÎ´’©ˆ™é'µ>€ÅÕ-àŒ ì¢Fçyœ9%ï
fèû#–÷ÖÍàØ"µ¹u%ñ›	-u%ÝnàJº]ª•~]ª¶å–®¬¡×•ÖÁ”üN,öë™z	Â»ÓDoS˜5¨NÓ{…
ÃlL«©ÇÕq—;¸ý5ÿÎê¥þÖëîÂ“þÝDo€=²éIÈšÅ105^Þª]Ûce%T!Cš~Úî·ª#sëbéE.«{ðåtO`æDíâ¡´M °5×Ë4FùGàÎi˜’„jRü©µMˆ¥(šùÄ	g]£§3c ³P²:WˆU«‘Eºº½¬i´ÄÑì•o²nYg®.ôreÁÕ¨Î2`¶¼ÔÃ˜éûJØnâ}(¢ê!+žëoÝå‘ƒjÒ— €mì’TŠOt×Æ1è˜QD{ºÞ­[ªÔÒ‹u)I8gZBhûhwÜ´á»"KI½{ËÛüFü¥+à!ÕúÖw«Z—;‰æ–/q¿´|Å	Cº”yTIJïwvTÁ~J?z5ÂåBFÇFø¡\Èh×?”M·ïÎ.Ré5Ä>ñ–7{tcÜ¾HS…Gd8o>µÍœ,\e+±ó%G#¸g>}Máý¨¤Ç®à%šF÷CxÇ~5èè
¿è¾0¾ÿ]@cô}(~EŽ½ù.ôQé-ØÞíp‰ÜUÌÛÔ3}ŒÆŸÏŽ¯rjHr4 Ýù·ðåhÅ¹S('ÿ
œª¥\rŠFGNx×G4ÆM»Ê^ØÂO æ8qãÇywÓóV²D¯'wd—®‰ðNkPÇxá—š £ïæ£7^‘Aý­(Iió;YÄPÒFÛÐ½*Ë
1ú†«efá2Ç™þÑ9>ó‚GçÐ»¡?Ú†ž†~·ƒ{w4½»"FçÐÓ¡Ä®ØÈG×KøNêM/n§>áí.·*¬=á.÷8Ú#–ÑãrsAõ[ÑñqÔ—©£±åþ–örô´„ûËÔÑÏ®ïŽF'K¸¾L=,áïV=wt¯ÜßÒ'
rÒÚû%ˆ(AÚ»#HN(
Ú#'H^`´GN¢PhÔ-K‰£>_…TF=éµzí¤×êƒÊ¢²U4ÿ,0±¸åqY_bâHŸ?§?
þBWU.ˆMß.d®¢Ù©ø¹²b?Y‚ÂÏƒýd	ŠØËNe%ýÌÔ÷
p~oº¡rÉxáÏ ²Øƒ9<¼h§÷Û‰;€Nh~™òNž†öJóñKéXJÞŽ¿slòçÎ–
³DËK]J¡í—Â\¸PæÍ‡v	SWØ	²K[9r;Gìgá1ßtv
[©—a¡°a©š­›Y×:ô´
S^ÔgfCcÂ[çl¿käîÄ[Ö3õ’Ðµç.„ñ£=ò…TóŽ}!(óŸrÒÍˆA"ÔbÏ¨|”D†‚BÝNæ7¶rëìÉX4°R5¾ùVóù*Ø$°÷q¹™ô”(§íÀòÝæ¡vsýnHã+Œó7,8>ß|Çz1‡;6ˆ9\é¸íAõ¸.¶RlêµÚàùìïDŸ½{Oóêó”‘›rìÃ;å„+:þ&§¿€ÖcKèXä¯_KK^£ãï€¼ù”çC¶usÌñ¼Èþ·‹œ¡—Éf.&zþªæR@½ÌM¼Hã-ÅŽÓÿb¶…¿¥&‘GÀ“¸Ê*zflI;÷Ï$Í×2Hl×ó“;?ÝÍþ>?ÄÆýQò=Rwy¹$$mÜ³dè”)G­o$â%Ò)ôQó1jdëz<:!ÓtßÃaô{²åÖ”yÞ&ŽjãHæŠç:Ç‚£’©å_^¢Ðßß%30Î}ˆ½ü‰ÙC-Â”f¼—W1…kl1[7—¢½ÎL@A
¶<ÅÅÍgü`Ò;Ó‘ƒÛÓ8ßkQ¤acÑ„Àëåµ‰¶ð0íò öJ@ûFQÞ:d6_þökÎ<ðÅI%g5°y@Ó~­ aEX¹8}ëÄ¸ÁëîàDàòæòÅU[˜è»æôf¶Çã$\ƒ)fžîàX'Ñ^?µºLH‰§^Ìâ”êÆ…‹ÿÁç‡(i¶_m‡3=Ñ‹MŽx‹Ç!íÎ®o7!üd£Å©u«¯ÏpÏÅÔ;‰nJç¸èÕ(ë%BçÄÐ=Ó†}3¡Ñ+eËÀ}ÈTð¬à5ÙkÌ–_:h»í¹ÇN‹/ž™dÖ´ûÍÐ¹,¦ë3Ÿîë!r†E3ægòÑ¹$iæx£‡Ã>ÇåEª	¯’öATÀílñàà³	¡·Ã;LUÜOføöøT,³Hm:¾óh‘Œ•G.ôòQÆô\Î„&u´3sß°¶ \;ýmH|á™ntÁ‰©é\ÐÏ¿iU¯@„Ä¾•¡¬3~C×ÊóûB„Ì°ÏIÓ±‘Ó¦§ÓëË™ý•¸æ{Ä7ÿj`ÜàÝÊÐ g¿ÁÛÄ°Àqƒë×4rÞà+°Àl;cË³†¯i¶@–@d€Ùƒ¤Æ[ÓAJëÀå
.Ô”
~è)”ŽµÄ)ÎÓóæ=¡þíÔÇ4Ãt{ø8ÐàØè®XdŠažÊ–\‰Ì¹\±^Œë7ö­ð!9°Ø¸pÅFqò+é{Ç
†™ëRòU¬`š®ãú®b8icß:Q·ZìÅ •  Ö‹qëÙ‰ŽÑ÷íKkØÄ±ÁÙØæ^|&´Qù^Ìà%‘gá€eéãzRâÐ+Åž](/)(ès((.›%zª¼–T„ç½Ã*y±rã;cÝÔ–]ÌyH®gx÷KìG6§÷âKá;µ8
­ƒN_êk	›Ë¹¥B!+aò˜ïT ¤H/»²ûø¹ô^~:ÉÔF
­éÙÐž·nlè‹xï °÷]Ö´múóºTž
þìž;~jÚóÏòðÃsÜÛìj“oÕ³ÛI¶o3½Û¥ºƒj?ØŠç¸Ëˆ¡Y$ö8f(hË€‰ÝÝânYûÆxç6f¨2Ç8~=`ëtÆ8ü¥æ®‹v\4ïPl†áLDïÅC%+`‡Þ‹JV4¬á‚ø®×ù€÷â½Õ0çÅúÄÇrz¾¯¬Tvô¢æ°EïŸs1T¸¨ìƒgObâH¸8ÎÅ´z^<©Ð3zÇ¯CdWçm¡«üUïs×;öý&±ëùÂÎ?Çõ"×´W³ôzR9Z €T‡Æ4ôA¬j:ºBñäõ~>€’qOûˆEÎÁú%¿sh¦§ß"4¾sàÐÁó„“{!f&ý~Ù©pÙïjôÓD
f¥2
z÷zïõ—ƒèHÍíÎ×Ýó<Ë7†íXõ‡æ~±w½Ô“^F	}xB$¾%•Q­'¹Fƒ™ùöÛä=A¾}´’EÐï‡ja¶t?¹¬x-›­ðzñ®ÁTh|ÌâŒ!–ž*Æoí£ut#ê¥uøø8Í¨xÞò–‹üÀ
9º”¾¤Ësèsd38tIƒÀ&>Û+2é—ea`ÅNÆ¥~'â²–0OD	þÿçÿøÇÿp}4      _   
   xœ‹Ñãââ Å ©      a   «   xœå—IÄ ÏÃcF@ì¿äÿïœQ6å–”«\« · Iü$Kt“ŸkHEq(Õ]hÎ]<Ýõ½{¦@÷Žf ÝGšt/4èÞÓœ»:î:MÿwŸ]°w:îyõÜó²ºóÙÖåoóÖIèš»nÝiªg²Ì{Ü;Íõ¤{ï÷ÿ®ƒ;sKu/§]‡“ÝšÜÜE/zþ­±ž—áàN“ÝŸvîÓ7„0@RÅ      b   Ä   xœR[Â0ûNƒš>—»pÿsà¤€ ®Ú¦µ«—Ø±ušäíÒx´‰št_'½vÌ%5V9é¼³Î
^Ýï,¥ôXêcL!ÌvSékûÚu`Ú:˜q ½÷šüçŽ1æLºŒ9“.c>™ê°®¾™bA
ÂŒýXžugç³]ÿC“ ÛÚ#ž£xçÄƒÔ!ª— dê½~HeI‚	½bÉäµ†Ææx§tu¦—7‹®u%ø~K)= t±^ß      c   Œ   xœÅÔA
1ÐõÏaJŒ:ê]zÿsÔa˜Å@w¥?ˆ<$ªd`²bHTM¨šQ5ejQT-™Z.ªF³N­¨½u&‹ºÝE½\•0¬„(–÷Ëý‘*øS4§Úfñi¿Ü]Ï}ts«uS¸XS¡°f­ï®ù×ÂkT~¤³¶ýuæíòißE¿_cŒ Ð      e   %  xœ•T]oÚ@|>~L´{w¾G$¨AÔ¦j«“›¸µj#pª*¿¾³@D ‘,Œ!¼;·»3{ìƒbïU>OÃ—¢y,©Œ”%<Š5û(?¼ú¥ohÿöø8ÅAË}Ù´›ªm$Ò(ËäWð8ðdª)$ß:£1DÉ]O²F2ï[Yoª"ñ±Šk»A°j¾¥OëbWIœ½žÅ*™ÊÕy>íìú¶Ìór|¿B®TåùsÆ¾YImÂX®;iÐdKSº‚	¢ ßÐâ©Æªiƒ´ÉP÷s`B÷Góé"-ê‡ªÅÿîïôðDÈ·_‹¦k
°ÙA}„S¦4ÐOƒ1 §LÚ¿éÏƒå€Eý»ê&ÏMWn6F:õ)3%˜6£4þ×nêÝêT†Añ‚¤øö°·W&‹GÌÓ-îÊí_bDDã`&"‘²7Î&~ÏÕdœî&ÃÛY¢xlÉ{2!¨À®ß¾Ð”Ûò„Wfc½Òžû‚Ç€Y§/i™F7ûGxâ–e·¤)hºàú %´Èpîªúåù©8ì¤ØY¨¬é|,!*û@+ÃþhyØx¬ŸÚW9rÊqæ.fjÞ€©	îºb›>—9¯öscdXc:Ú5Vâä7!Òo‰°S¹ÝäfÀÏÚ?›²«wµÈ,'†èŒ“Å	V[¾¬‰.©¾ßƒÿŒ¸Ù      f   
   xœ‹Ñãââ Å ©      g      xœ\KÜ8’>gÿ
]f/ƒªŸ’Žõ°Ë½åìN8ÛÝ»À9KmÎJ”Yn»¯óSö°˜¿1óÇ&(¾Df„Ê€Ý®¶¿ƒÁ`¼$[Õ¥(Ëª,ëÕý…d¢`eù~ÕÔe¹*Wlúoùƒð(æQw»…ªüÖÒÁ$«ŒI]®t)kTP”)Ì\5¼tPÆ‡ÍênlíC[<tÅÍ§a7ìÛSg®EÂ0—rus¡Ü¬X

l”zÝºIéù¤˜>C¹9UÉœXe>\–‚)µºzW\‰âzlÿ|Þµö³0§ùgë³Ïz	¨LG
1—ÀëçS÷aØÛ©U*™g«¦”“„Õê¾?ëî¡ß
™àÌp*™,çßAg§o>›>ßAigÈ›l†\®ªþ•Š¯^·‡©àj•°¨<–öêqø\Ü?{+æ¾ä ©/»5¬ÓITÜ­
gçµ' ‰ßwc«¨3ds†´,¨TŽ¢<ÃY!$Ú#˜GÉfõêødTâjl?tÅ«‹íÓ0žÃ™¨‰Ðq•nXÐ¼È,“UÂdXV)Vëv÷©¸»Ä6™P8Ô1#Rfì%/Ò)Ë(+–òŽð,9FåhÀ2 g«Ûçv_¼iŸ¸:JiáÂÀ7Móo®î’¥Wªðan?|{ñªý¸ïü‡Óý.ƒž3Drs‰Î°6{4ÜX«Õ/ã°kÇâ§á±+†âf{î½¡cß8<øâÕã‡}÷Ø¦ÌS€Ê	c	U	{³½cÓ¢Ol‹”mÅ<ŒàíØ‚à†/­RéÁžôV®¶7¸*î†ýf_•X†KÉÁ~nš²X_ÞÌÁe–Ž›îæS÷íÔîŠ5ÐÏ)+6Þ™;³M£¹{;œž˜eÕÖRpat±øñ Ëy,6cw,EÕ$M 	Ø¤ã£¨Ê@!³1Ú“7¦ÉÄ+(TBñ¦Ýï‡Ã]w@âL'd°cúÃ§çN¢*k÷£ólW±K~ÆðXl/­JÀ› ‡ÅŠðÔFÕ	sÆjÌØ¾í’˜®4|¢0ûµ²;óýŸ}±í÷Ýa×s(c#MciÖýn.¾ƒÒkf©Õê-cêŠ×ïŠ›öq@ì 0·î}qõÕ›™î¦¦Z™¿)ÁÌÀn®¶SÅvïV!Qö&D ÀÛ,iwÏÆxX>dÝ”agƒëp|§ËÐ¤xî¹1ÊÜ\0…[ •Æ¶­o¶Åo—ø$ÁŒû}

þÛ¦ØBÀàÒäPåÌ‹±¡Û»B©tbB0eBß¯¾ž<˜§¶œ±(êÚŠÚðŒÅš`LŒÙ9ÃÎ¼³»¢ž«{*e×(8w3.H0äñ7—žˆ\ÿ8©;.m™¿>í&%ùùxÂÇeþñ&l=ÛvŒi7$	†Ù¤¨ÒR¡3(ŸSÃš¯®Ûlm±®9(#Aìüó’‚Oâ4''„-Þ24icÊPí-„Û-»x§`3C€Ñ:<f`’)/£CA‰Hò`Ñôêç«‹FÌXªnRàX«<š§³…èE;á‹:›«lü\1Ú¨ûYÍQÃ
rûÔíNc75ËÑÞh›Í6nÇU¾MdáNåÃ†Ë-j²”òŒ×úóeÁÅÜH•ñ¡= ½ûnêv™›éç« mé¤ï:U{ý`,êGî•¶ûK4
Õ1X«wòtãc{<ucQ]j^l¹þï°»òÖìeZg‡šTÌš¿L‰xk¦Ã~ÓwNçmrFå"®
Z-a*¡u a)É%lÒÄêj‘Ì±—Ù(§¿½¹zwñ¶x
1.²0%=Vyì»n7ÐYTe@K5™(Ü­TÁG°™[ÁÕµRfCKÇøº=BÑWì])c;¡•pŸ›þðÐ> ÷ûþ@³
VÃ#\Ýo+ù>%È
J
DEï×©R|™
P‹€¯ƒ¹JGÈ)T h¼ÝOr«_‡íÆó…	4~À%­ï‹K°E©ˆ2ˆ{ÝÃ@¯[P·âŽ{ñ¥ó]j'š|1µºúé‰zˆtÝwÁHÇïú§ðÝÔÌŠy	 ÷hÄÓø Íèô/ šœÍÝ[j-`õ½e™eôeˆÌèÂrz9B<Ò;WS9¦¡ÙÊ>Î-ÓÌÕ~¢Ìâq3ß²^Ý´Oíe±}ŽÂIö-pÑ•C·_ÚÃe±Á‰C´ðÚá!Yí¼Ä„ÏKñ"ù>RÝåÀ°ß¹=ú{Û†ã±}†¨
+spèžjªMXªM»ÿÔîtÖ,¸rž;ÌpÜd¤¿µûÓ'äoWfÑ	ù³àßÁÿ>Sžt¶,¦ ð÷ÅöçÍúç[<Èà¶ø;)èý›âÞûá	Òt_`,])L8—õ¦š±<«ò`mL­á‚E_ž¦iœKè¼GVèä
:ä±ºTÙ²(’»ðX<õ(Ô÷óX3õ8ïÏÆ¤œ„4¯2Èj&xt+ýÇ±Ã
\pïøVY[ÐTÑWÈ¨üÍLù>ÛÏ¹R4žàJÓ$WU¤©Í¶GTé65w\ÉŒ«†¦ r5“º
'ëp€²o}a(3F’Qh4šã’Sx¯}"ç'l;0|6(ˆúWgê'Ã~*Ùä®#´ÉŽf¤gLÞpu!½æ9:„nðáíÝ…©JÌà™_ç*ˆúZšª½gTpÖ`¤-'ÖâŸ©+¬nÌºæK”ªjðUÒå	>ó˜†Àv»Ý¾kfgŠÅìü¼Þ^b!0	Ã‰›Ò˜'Ì±Äù)ìõí¯ï	?Ñ½O	t¨û‘’†Xˆ@ãb®J
OdPÜŠ‘ÒqÆÝ©Á4±¿‚Ò®»Çãp,C±Û·{h`s:¼zµÙ°¦¸îÿÄ3^5átDN;ñQ]fU]ÙTPd,Ù"‰‡DÀ%éà‹\’ŽdÍ¼ö;9ìu"Ï,b-i
¢:Æëâ•w4øÞl‚íÛîwècà?G¢)&1‚¥ŽBCèoªŒ.4·T)ò‡û¶ìG$e_5E­×w’¡ZÏéE8E²ÐÜ¨7µ‹ê@åêpa‡Óó¾-bÍ&ëšfÂN²bÙyo¹@âf«3ß;+Æ›ÂÆ›$S­°v‹‰×‹WûÞ7 ¤ú!Ê:€¥\½ëúÃïÃ¸ë ãnŸNÃˆÓ4‘FÍi¶§Þ‹	+#‰ž“\ízôˆòNR°*†i£ K)ø…S¹´Æ)˜X¢ñÖ±ÊÕm)™Ù„”jò¡ªüK¡|rÃ,è(D¾Û;ãÊ“ä2SUÁcœZ®îÔý¡}ð‚‰àÁn@ôrj$Õ!Âf©¿MúVR\4H{ªÞx–º[!x@²	9E2'D¬-×6e!]X¡‚«0…åÆ|/	kG¾lá¶¡Êê dÁ>ÏÚ™ò\.ø‚$ñO9O24!Ë—¨œ%N{‹„d/Ñ>DÈó”!™Æ—@ÊÅ*$¦°Û}M‚Õu•Í^¤pMÂ‰iW$á…„œ25µDÕ>ýëïÿüÇsq3üñaøFl…øÔ®™m´ÇáÐèÌU´F°ù=ä\ëaô–5Í¢„Š'X&c$ºC”ŸÑicsûKÌÜÂ4Îò	Ô^Pt[AÍ
é*¨Q@”¬ÃÍðøIãtRÍÕçõ?Âƒ·
P½z=cÍœ•òœ!¬ýI‡ê(“Ñ´¤û5µ:ä°ælÚ/Ø
ˆVø]“Ø&ú‚×ÏÏ„MÊ;ùdPÂ›ËbóéÛ	ØdGèT'*¶H‚ïŠŠ/Õ¶š]ãÂ›{Èi‘€YT
EC}QÕ(ØûÊÜ U¡T
ÚñîºJÛm½þë+(‹º$áN:™¯I@ÙÈZPM_T]+bõÊô¯ôÇS¿+îýïxXUWÎ#Él"õ‰Ï¦Ò„<ÍõYü-j’š’Bã²m…§Õð@Áæè¡‡h•ebZÚ„¦Áé¬"Íä<53`±5¬ïºÿj[cnÑŒQ@¸å»Yå¼½+o‹J{¼ÌŸÞM³P¹NxjR|H°ÎOÚ<_Úú¾rÕ »a‡â§¡Û£
-’•!I&jœáâ*òàk Û‚™Ûw§–žàæº¸}=|EiKè9Mƒ$Ó–Èä¬Þ„€~Û
Oíø@ðQh‚•†€SÜð˜Âc@ð«9îz×ìpFÁq~8§ð$C"Î 6S†ˆ3#1(ÁˆÂ°"œ¥™³«à¦Ð†­Û/ó9øÜhIÉP(ê+¥ä(˜0WR†þ(3Á u¥2åDRhÇL“1£(<á™¤Ôb.Ã;JŠ!)1ÖÖ÷Ó2¬EÆ&š*’£ñ™Œã¹•rŒ—¹ 5[·\$‘é—æ‹DÈq†œÈv¦G$RS™&Z“Zpòûãÿx"åì4m³•$à/•^ÊkÐpNVÕ
ÕÉj!}Fc	Y545cQÑóFY³E"ß½VæcñC ô"Œ¬Å‹„Ä=YË¥®rb¸ÅNtr$mëórªy¾ëŽÝ	dñ[øÛÛáØG[ž×e¸ ¬%hæ÷ý~ÿ·Û®=}r"ø{åœà¶;B;5¥ù1X$ñW
D 1÷ç|…cU*¬·­'«RcX¯ ™²™½:qSOÐæºøñp4­>¦jì¤-¹3©Øì¬7–®>†±Å<™bj‰=ºQL/ÑÛS±¸©ËØtõzß>úZE•rVÓxô"Œb
MAœ°‹æ4—ÅÕ¾‡Ý§L\œ‘pôFžâœ$ Åã!?¬N ¹Þ?£EÅ%'˜R4É•¦º†œM¨³1*
ïGÈ•7T'!5ªæF'ºX”mÐÀ{“Ðp@	NSP’Sn”lC	IS7Ê”+@e¨Rb±H•¨¾·¹õæJ|ws0‚*[ôóös\ÁeIP†`Öâ~v
€„Óä(ñ~s¡k{§É(ÉÉ %‹·~ˆQõwSc«¿ˆÆbJ1MíeÅ±uüª·–(R*[fFÎ*ñÛR3'ò¥åòñ&1ŒZ¦"GÓ‹£Ä`Õ"9ÖìàöüD•ªY¢¡Fªb]é¬Ù-¨ŠÑ>üÊ5¡â‘f~ÄMŒ p4ùõè·Ë˜åü4íþ‹¯6&µ=5ë[G(œ|EÆ•^¢!áäRþÎZï¬ùJ¥jR¶Œžo›Þ%î…:7$u|I@¬ œ;~*6{ßÕªÓ+·³”)ÁâÑø,OJÐž“*ç$^åóx†ô×)HmüwË•Íq…c	ŽkMrÜ Ì—D`ß”(˜hÈÒá¶âÙeh ×  ÷ù”w.,žá‰ÐC—Õ÷uQ×eýaVtÙ¼t©•/ÑQ#²ï¸ýLŒÉ_¦$G‹·´Ñ†ZÍä"‘Kçc©Å;äÄäô"9¯¨/Ø
wb¬åkñÔXœãÍ‚¸î‡úM!æP8XBc5_˜ÈñD!K‡'ðÜýË4æÕáµœˆu/ybWÜ‰S|]©¥#v´ž©c'FC	£ªDÍ¥®|7òÙûä„Šá…Ç"¶HDñÖ„úÚN‚f®º©‰ˆðB7³Þü´MÃÍ™'îTå¬Ps~å‡…/Ñ#Å÷WòF`t«V¥$	ˆ’BÃÕyO0šF5\Ÿ#	¥ox•_>ä/²¯×4aÉšÐ³÷÷¡:Ü¨å¦@B‡›x“øüð5MlÜ?§ îÊ–ñÎ×ù‹øMY_’$ô8¡îüüÂ°	ÜHêjr9»Ý5¿qNãñêø=ëR„Ó¨xÏ
nY)ªs¨M„²§=âUäî(švL/5Ñ4ÄÎc&Ùž÷lBÏ1[©<¹Ê±%1mœCO“^ápb—›ÓpvšÜÒF­Ó? pUgß$ÙÍnü‘º2ÞùÉ	ˆ’•ñ>ø¼õI¬¬&
I¬¬ÿhïê+€J,Re[ ‹—Ïo'š[©Rs«ð>ÌÙµf4ŠŠ¤ ^7)—žG"¶H¼ê~NBÚœx½„jE³ d/ž1›MÀUß›ŒêÕ7HÐXfZMíÙát>yÓö_§CÞ+ÓÃ¼šwá3Ó|¿åÆ2
‡åþ”Z˜Ëzî
L7Œ»áÙ€MÛJŠ‰o6Q„þx‘F³s"³R¢ÐÓÒÈÕ{Î‹ŸºaBåÜ"Ãs&µ\Ýtã‡n|>f,‰üëáÅ¤Zx«•°£s‚%A¦±Ý
ãSâ×?/5K)ÍþK)U˜=÷oÄ$Cñ¦ƒ€™¹ƒÈxJ ÎäË¨foÆMUßl=¤Å‡›tº^ý×Ú^÷1:—½zÁbGâ‹müJ¹nªš}åThûüøØÙü,¿2Ä7$YÞ
d–í®ëÇÁj•JÛTM/o†ý~ø£Øýá4U©¼p˜ƒ««i.Q$Î,7Ö³'ir4ïf,†Ÿ9ºáö§yf³¹‰úRŠ™o/ážÜ@ˆ°·!Ìã3n|í6²ÆˆçÆHËÐÇZ¯îŸm5˜3óÄLŽÃŸ^2/ËäHï¯ó˜ƒéØ	?Nµðíiì?ã€Ì½$3ý‚§æÂå×˜{P½]ÃX83ÀÆ h5ˆo9<S…Š/CSùþoó ÚõóéÔ¿ï¿Í»¹Ó›eÌ<xCS¸%ùtÔ_Ì³=W».äÊø\g¿ûì3ïÕêP„2G
óûé+€ä’ØÁ±5~†õMEgš/¹Bðç½eòÆU¦Gµ¢	¨7ãX­i"ôò-›ž»1åÛqn]¾ñƒ»‡l;yœ‡i8	Ì§ò«’Y«kú¨ÌiÝñ©ýcjrýKu¨’;ó<Ý¼öæŒ•O0V²Î™q#¥øA5ãuifŸ&œ”³ï±	ÖÌ‡Õ6ñ·î>¶Å›M¡Î¾VY˜¨Ã
F3{…ÑIÇ!k‡œžT|õõÉO6E5¥ÏœÑkH‡ûßû]ûÐæT¶å
¨”ûö~8ö_ã6ÆÖòRÍáNöÂŠ@Û§®{ÈANîÆU¦œd’2W?' 3Àëvo_ÙîL“}v““MÍ^¸œI_åkÎÜñiÍ<|y>tæ­¿}ÿÐ>tÙ0·R¼ž¯;S$æ–ŠWVAvæÝÁícw8
ÅØ>õŽßäãnÕø´ößwÛ"X·vl`ß‹v´ÏýOÃêTîìTZ3ˆË¦räcï¯Ž»lêæšð“¸.®‡ÇbÓÝÃ0æzÁÝ–“7íibáu»?¶ñ‰ÿ®[Ær£†U\?úýýŸÿ¿ÿoÈäÉÝR–Õ|Ã	»áæ8·˜Öÿ_=u{#iXúa„‚29.ÜbÚ{—³ç•"Ù[ÒR¹¥-eØ…ÂoÂù
q·š¥ð{¹nÌ¦¦®	Æ=L`0aWŽK3MŽ}»·›.ÈÀN+¼;ÎdµºoÇöñCB]¤
/'PÜ7ªð¾x¦œ¢!¾b®ÅhûÇ0>dÉ·X_”cTçn]¼sêxÆ‡ë Ös0dª_—9¾
G2æ’æîÔOÝ'¿Ø¯Ÿ¡kçXXt,kÈ¾Y'4×ÑPPç‚Êè‚¤õWÌ¶ÍZì¶ýü<¶çÎÍ4AQ`ûåjþe»5X=i1Ã÷’_ÿŸË~øáßž)a      h   è	  xœšMrã¸€×ô)°ÊfJ*ü’ÄR–muGÖŒÊlO'©T¥ØÇf5Mº(¹ÓÓËä¹B¹G¦*çÊƒH‚x¨žî%>=<¼€fQJ¥	¥i´žI&£ô1b§ÿôŠŸ-+wYËlX^vKü´,ËÉ¸¬Ë‚Žëñ°Î“hÃ$Ù”uÕKBÒ1{­Ú¼Î÷9ÙdùÜìš*?zÿŽ¥[P-gÊ&aYzËøÇöü4>­Þ¸¶cñÙªc:–D°¥‚)-Wd!Èu›{ÛåHHz&Ä50ÓÃ²îiïÞŽÅ§¦òB^†ÑÙ8‹4•'ßªh]É¦Ø—»Æ³ü¨	ç¿ƒwÎÏÅïàÝ£rA”PÊ¨âÑ]^?…ÌÅÕ ¿/Íg²~ûÜ–®xzÅã)Q'{$SP§UO¥[myÀJë³eÇ‚ž­:glX•:º=¼o-ÚüSAngÙkÓÑN‚v7ßƒ]=¬á¥ˆ6ùî¹ Ï¬æQaÄÝR‡÷’†½‡SŽfaXw·nñ)ÈQ	‰`…,ºyË+ò.¯÷Ooµ.‚_IÙqÂp[­ÿðn±FˆRVïDÝÌnó§
'!®¤<¨,ƒ–È–2Âÿb
‡øKóò©,HVå¿-¢ÒôØ4E$úÐ6»¼%?6/Ù7dYAR8Ó=Ë-Kn_>UÅK …Á?E!ã¶ÙŠ|=ž‚ÅWŠ
¥›6“5_|L^AÞô%ÎÔ—¸÷õ/E[7îQ”ˆŒbà)ÈË5$ÁdóŸƒ¤öMt´|.~=æ;²a5“\c¹oŽo(Ïâ.…¹0¾Ë ô€4ðÜlÛâˆDÆÚ’‘PHfB-)=™ùU¬„YR!ò]^UMý÷¢¨Î-#‚¼¬Ÿ¬…°p‚õ5²wŸ]6¥½(òÂª©ö.¦-q2b²¡ÙàVá’«ìžCð#’ŸH–5OÉóø­$YYõ®4™ë²Â²ºc7å®mf~aƒ&VÑ=cjÁÈõYæ/È·Z
êBŽn5%·_s²½~¿<S×æ0¨óJI_Qžs}¥mÃma
²‰±#Ž£»¦ÜAêædVD•LÛíÛiÚùîÍ¤¼;*P›–Pßû“ÝfPÎ„1(7chî	0rÈË[’A5F‡” Õ'¸©fÙŠ(EÁÇ.•[¦/;Ëº¥Âyl¨ÐöúZq¿øðþGTg|ð3^ÚÌ—ä>?–µÇ	ët9˜"$.,!R?Ó4	zœ±ÑiçÎÍ2ÃDj£]F?-fZøS¬3àáa&Ç,g õvj4&«Y´ê’8%7¨ƒ0˜ÅÂ;r1¡ù’KK‰èýæý)5½[Oë.e˜2w—ïNüÓáÐx›M·>¤y:‰aqÚÖŠØ©ÝêS0Y‘0a#*åÑuÞBo ›”C\!QrŠr ãÒ…·'Ð¤›@mŽ‰!òÌ`•elö  ¸Á¬sv×bB_@±Ç$³¶Sƒíêræ›NÚ|qö~Ç`R„×"0bd9æw:Ê¦Ü×åÓ3®qÒÕé­Z{ã	7·7ÛË —d¯ÅîØäã9642SÀÆm]JÅÃAäžRIÛc“¡zÍqQ6™ Jo>Ï	gõÒ`cá‚n]TÇbê¬Ç/Kž tð3c£ŸýœU¸À(m1}Ì«ã3äÞÇ…‘äÅQ<N“"z€.Ú—üp4=9É>\ÿ;9fßÿkÓ˜ŸG—r›ÇP%Ïy¬‹¼È"5ÔEi[”at.Dêi\d‘éÐga@É–‹‡Ù=¹ƒîˆ¶Ö–QóPì4b²„ZJ”‰S•@/¶70§ƒàøJ`D`&ÃNjmò-9;HUùä0'˜n›­Ì,ñPTM¾÷"*±'Ðs·e½¢=é$èI´µT\¬³D>†%Ž3òˆ%¦¶dÀ ø¸ÙJ5!Oqž<a¹ÔVª°D9Mz2•%õÐÂ"ãIÐ“h‹
\3¡æNˆKÃ”'K±Ír³&s¨ƒAqzijš$dYqS»¾à3Óö6ÊT´øñoWJ¸Xôr ÞrêòÕ—#-ÈGn¡x´ÔÊÎrpç†â,Ü©tl+°ð*0~da#S6ÁÆ× >Å¡€@ØxzÄÔ–q–ÐÍÛ{aä&Ý¹±M£eþšÏIöæ™v©¤§ò/y
÷-ÌÉ‘‹{nÚÒsÌ©‘H¢R[ŠàÒ=”¢›²n‡ü
æBï(Úâ§·šßæÕsþÛ?ÿ÷¯ßþñßÿ AŒ3Û¹˜½h®0Á§Û&ÞœÙ4†j&ªâÝûñÉw°ïJ¨×Ík~8àÇ
ÎlqƒÆ´Ù&þ`Ë¹­-ædÆüfÏ¹ îK.W ï1>{õ“,Ú ñW‘ôÔ_Å¢ÇAOžÎw>-qACŽp¸vî†éÒ6ªò©ÅÏÜ‚Osèy[Lsè BŽq¦8«ñ3jšCÇÓÞ8ÁÔ‚Ìxà"æÐÆzšÃùv¾€‰~øôQåø=ŠK6E¹›J>Eá-mCèm Nì-Ä£p¤Hî”XHRb<9v`ƒª¹XÏd0.¥Ù@R¶š™¹(°¡¢–¦¬Q¡Pn¤y 
ÈâAÈ“dÛ ÊNûSò({9…èXÛ»Ó¹·•¾ ºéù|¼I@ŠÝdP˜ð9Ç«ƒ°öã]:jà—>Þ\é«BVÔ^ Ç³Ÿ}5oÙS2µW„Ø¾ožÙ7ÖS”«lB§(¤pÿfxÎAÂxÿÙ0ý ¹)^>µÍÔ
ÙU}ý·ûí'±ãh»eš\—ß¼z”ïô {3»k¾’8ýÓÖ³[7ÿwwé4º/ ;¶{ŸÑö»<
_ýW<yñ~ð7¯!r|¡F.äœr´.¦?÷ºFKå4‡|Žó¥ÀÐÛ%Oã Ú:¹ â½må‚fÓ“î{.DŸ#8nµ­XÂ~ÂãÒ8Ú»„«²é?ÀZÃÃ ÓÏáhy¾Ž¶Pçëxk_h2w«™ä^ŒéÑ®ã«®‡¤6¤¡®~€¾Yßªœœ9Së ú²L/€è»1eã )ºAÒßVtoøÃÕã¡(ë_švWìÍ§ú7Lž÷c®ÉmUâO‚¦‚–ëˆ{È_M‹Y=²hëìXâ9R0:¢±‹.vå“vØ3¯Ã¨ø{ðú%Òµ8—Hdr¸˜É`KÓ­o¿¾VÍ¡üÒ˜6ÛöÛÖqOóG×yÕýÁFÑ¶
æ’®ÖÊ„:ŸƒKÓœ¿õai'%§/ÙÅ@yÛ}n^›º¨Gubÿ:¿ººú?Ìmˆ·      i   m   xœmÏÑ
€0ÐoÆ[ÝÅýçhLÄÚ/úr!HáÏ€N‚ùj1í@«l1u@*{îZ–ˆó“’~XÛ²ä€ÛXÒg”vÖÊ27{÷?×rgºdÁe½ä™
jµM~<nïøµ1ó
9p6      j      xœ3æ450à4\ÆHì=... D?a      l   7   xœ3ä4204Ö50"c+ Ò60	›a.á2"Y‡1É:pë02Àª#F‹‹ â%2     
