---
layout: page
title: "Tips with long scripts"
description: >
  Making long scripts less of a drag!
tag: [blog]
---


Working in Healthcare informatics means I have to work with a wide range of healthcare providers and an even wider range of EMRs(Electronic Medical Records). For every speciality of care, there is a different slew of EMRs available which can make it tough on Dr. Doe (hypothetical provider) to take his charts from EPIK to BasikEMR (fake Medical Records platforms) and access them in their new EMR.

Lucky for any Dr. Does out there using gethealthie.com, since we offer to do all the heavy lifting to make sure any charts they have fits into our EMR best we can no matter which EMR they used before!

Lucky for me I get to write a new script for any new EMR that we've never dealt with before which, in the wild west era of EMRs, is quite often. When dealing with big loads of data, these scripts can take a long time scraping the information from a webpage, parsing through long tables of erroneous data, and creating new objects in our platform. It also take a lot of trial and error when it comes to EMRs that make it hard to find the information you're looking for. Here are a few tips that can make writing a new script easier!

1. **Make Comments**

  Writing a long script can be tedious but trying to debug your script can be the biggest pain point! Invest some time into annotating your code for your future self or a colleague who may use your code later on!

  ~~~
  Example:
  #Here, I am using the selected_private_notes method to generate a string that I will be using to write a pdf file.

  #arguments: provider_id will also accept the organization id if applicable
              dpi will indicate the size of the content on each page of the pdf (a recommended default would be 400 but can increase the integer if larger font is required)

  def selected_private_notes(patient_id,provider_id,dpi)
    user = User.find(patient_id)
    puts user.full_name

    # select provider or organization
    provider = User.find_by_id(provider_id) || Organization.find_by_id

    pdf_binary = ActionController::Base.new.render_to_string(
        :pdf => "#{user.first_name_last_initial}_private_charts",
        :template => "users/selected_private_notes.pdf.erb",
        :layout => 'pdf.html.erb',
        :print_media_type => true,
        :page_size => "Letter",
        :dpi => dpi,
        #remember to add any additional variables needed in the template
        :locals => {:@user => user, :@provider => provider}
        )
  end
~~~

2. **Use Semicolons**

If you are running your scripts in your rails console or irb, you'll typically end up crowding your terminal with whatever is returned by your method. In the example above, my console would be crowded with an excessively long string. There are plenty of ways to manage your console but if you don't need to see the result of your method, you can add a semicolon to the end.
~~~
1000.times do
puts "Hi, this isn't important"
end;
~~~
Additionally, if you'd still like some indication that your method is finished running you can add a confirmation message at the end of the semicolon
~~~
1000.times do
puts "Hi, this isn't important"
end;"Hi, I'm done printing unimportant string!"
~~~

3. **Audio Notification**

If you have a particularly long script that you're going to run in the background while you work on some other tasks or cook some pasta, you might end up forgetting to check when it's finished(your script, not your pasta).

We can use system commands to announce when your script has finished running. Using our previous example, I can have the system actually say my notification instead of printing it:

~~~
1000.times do
puts "Hi, this isn't important"
end;system("say Hi Im done printing unimportant string!")
# system won't accept symbols so I got rid of the comma and apostrophe
~~~

Once you're script is done, you'll hear a scary robot voice repeat your string! YAY?


I hope these tips help make your lives a little bit easier or spark some other ideas!
