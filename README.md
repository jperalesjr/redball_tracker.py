# redball_tracker.py

import sys
import time
from naoqi import ALProxy

IP = "169.254.113.113" #replace with nao current ip
PORT = "9559"

#added code
memProxy = ALProxy("ALMemory", IP, PORT)
memProxy.insertData("myValueName1", "myValue1")

print "The value of myValueName1 is", memProxy.getData("myValueName1")

except RuntimeError, e:
  print "error insert data", e
  
#added code
memProxy = ALProxy("ALMemory",IP,PORT)
val = memProxy.getData("myValueName1")

speech = ALProxy("ALTextToSpeech", IP, PORT)
motion = ALProxy("ALMotion, IP, PORT)
tracker = ALProxy('ALRedBallTracker", IP, PORT)

motion.setStiffnesses("Head", 1.0)

tracker.startTracker()

print "Tracker started successfully, now show a bal to Nao!"
speech.say("Show a ball to me!")
print "The tracker will stop in 60 seconds"

time.sleep(60)

print "Tracker is stopping..."
speech.say("Alright, I'm tired of that.")
tracker.stopTracker()
motion.setStiffnesses("Head", 0.0)
