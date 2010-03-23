# dm-riak-adapter

DataMapper adapter for the Dynamo-inspired key/value store, [Riak](http://riak.basho.com/).

## Install

Requires that you have Riak installed. You can download the latest release [here](http://downloads.basho.com/riak/), or install using [homebrew](http://github.com/mxcl/homebrew):

      brew install riak

Install the **dm-riak-adapter** gem:

      gem install dm-riak-adapter

## Usage

Require **dm-core** and **dm-riak-adapter**. Setup DataMapper to use the Riak adapter and define your models.

      require 'dm-core'
      require 'dm-riak-adapter'
      
      DataMapper.setup(:default, :adapter => 'riak')
      
      class Project
        include DataMapper::Resource
        
        property :id,   Serial
        property :name, String
        
        has n, :tasks
      end
      
      class Task
        include DataMapper::Resource
        
        property :id,       Serial
        property :summary,  String
        
        belongs_to :project
      end